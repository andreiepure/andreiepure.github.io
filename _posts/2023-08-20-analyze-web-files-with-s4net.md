---
title:  "How to analyze JS/TS, HTML and CSS files with the Sonar Scanner for .NET"
---

Imagine you have a .NET web project, where the backend is written in .NET and the frontend in JS/TS with HTML and CSS, for historical reasons (because now we'd all use [Blazor](https://dotnet.microsoft.com/en-us/apps/aspnet/web-apps/blazor) for the frontend, right?).

Let's say the layout of your project is something like:


| Folder  | Description |
| ------------- | ------------- |
| /src  | all the .NET code is here, with the SLN file in the root |
| /frontend  | all the web code is here: JS/TS, CSS, HTML |
| /frontend/build  | some scripts |
| /frontend/src | the actual JS/TS, CSS and HTML files |

And you want to analyze this .NET project with Sonar (SonarQube or SonarCloud). When setting up your CI analysis with the [Sonar Scanner for .NET](http://redirect.sonarsource.com/doc/msbuild-sq-runner.html), for example with GitHub Actions, your `build.yml` would contain the following task for the analysis (I skip code coverage generation in this example):

```
      - name: Build and analyze
        env:
          GITHUB_TOKEN: \${{ secrets.GITHUB_TOKEN }}
          SONAR_TOKEN: \${{ secrets.SONAR_TOKEN }}
        shell: powershell
        run: |
          .\.sonar\scanner\dotnet-sonarscanner begin /k:"<NAME>" /o:"<ORG>" /d:sonar.token="\${{ secrets.SONAR_TOKEN }}" /d:sonar.host.url="https://sonarcloud.io"
          dotnet build .\src\NAME.sln
         .\.sonar\scanner\dotnet-sonarscanner end /d:sonar.token="\${{ secrets.SONAR_TOKEN }}"
```

This is because you need to run the build (with MSBuild behind the scenes) in order to trigger the Sonar Roslyn analysis for C# or VB .NET. Unfortunately, all your frontend code is in a different folder and, even if it were in the same folder with the solution file `NAME.sln`, the frontend files would not be referenced (in this example) in any MSBuild project file.

There is a small inexpensive trick to include all the frontend files in the Sonar analysis with the Scanner for .NET. You need to create a dummy CSPROJ file which references all the frontend files. For example, if you create a file `src/sonar/frontend.csproj`, it should have the following content:

```
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>net6.0</TargetFrameworks>
  </PropertyGroup>
  <ItemGroup>
    <!-- Import all frontend files for the Sonar analysis -->
    <Resource Include="../../frontend/src/**" />
  </ItemGroup>
</Project>
```

Make sure that you include the newly created `frontend.csproj` in the `NAME.sln` MSBuild solution. This trick will tell MSBuild - _"Hey, please take these web files as Resources"_. The Scanner for .NET includes special target files which, during the `dotnet build` process, examine the build environment and include all items picked up by MSBuild from `ItemGroup`. Afterwards, the Scanner for .NET tells SonarCloud / SonarQube later on that those files need to be analyzed (in other words, the scanner "indexes" the files for later analysis during the END step).

However, we are not done. If you run the analysis now, you may see in the logs of the END step entries like the following:


> WARNING: File '<WORKSPACE>\frontend\src\a\b\file.js' is not located under the base directory '<WORKSPACE>\src' and will not be analyzed.

The good news is that now the Sonar analysis is aware of these files. The bad news is that the Scanner for .NET considers, by default, the base directory of the analysis the directory where the solution file is present. And all indexed files need to be inside the base directory.

To fix this problem, you need to explicitly define the base directory during the BEGIN step, by defining the `sonar.projectBaseDir` analysis property.

```
.\.sonar\scanner\dotnet-sonarscanner begin /k:"<NAME>" /o:"<ORG>" /d:sonar.token="\${{ secrets.SONAR_TOKEN }}" /d:sonar.host.url="https://sonarcloud.io" /d:sonar.projectBaseDir="\${{ github.workspace }}"
```

Bingo. You should see in the logs of the END step something like:

> INFO: Sensor JavaScript/TypeScript analysis [javascript]
INFO: 1071 source files to be analyzed

At the time of this writing, there is a limitation: the file paths will be a bit ugly in the Sonar UI, because they will be relative to the root folder which contains both the `frontend` folder with web code and the `src` folder with .NET code. But hey, you now have them all in one place.
