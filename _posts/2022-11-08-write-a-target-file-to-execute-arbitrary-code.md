Write a target file to execute arbitrary code

## Vocabulary

MSBuild is the Microsoft Build Engine. What is less known is that it offers a scripting language. An MSBuild file is usually a script.

The MSBuild scripting language concepts:
- *properties* are variables; some are predefined by MSBuild during the build process; others are environment variables; and others are customized in MSBuild projects and props files
- *items* are inputs in the build system, usually files - these are used to include or exclude files from the build process; MSBuild has predefined item metadata
- *tasks* are atomic build operations, like "compile" or "copy file"; there are plenty built-in tasks, and we can define our own by extending ____; a task must be present inside a target in order to be executed
- *targets* are groups of tasks to be executed together; they enable sections of the build process to be called from the command line by ___
  - targets can have attributes that specify the order of operations (`InitialTargets`; `DependsOnTarget`; `BeforeTarget`) - MSBuild uses this information to build a Direct Acyclic Graph of targets to execute
  - each target runs **only once** in a single build

MSBuild offers an XML scripting language. By convention, MSBuild files have a limited set of extensions. However, it is only a convention - any of the below files (or a simple `.xml` file) can hold the definition of MSBuild properties, tasks and targets. That being said, by convention there are three types of files:
- project files (`.csproj`, `.vbproj`, `.esproj` etc)
- target files (`.target`)
  - The `Microsoft.NET.Sdk` target file is referenced in .NET csproj files (`<Project Sdk="Microsoft.NET.Sdk">`)
  - The `Directory.Build.target` file is picked up by MSBuild as a customization file in the folder structure of your project
- property files (`.props`)
  - The `Directory.Build.props` file can hold build config and is picked up by MSBuild

Tasks are normally kept in libraries (DLLs) which are referenced by other files.
MSBuild files can import other MSBuild files. Usually *target* files reference other *target* files.

## Run any code inside a target file 

Let's write a target file that opens a browser when being executed.

```
<?xml version="1.0" encoding="utf-8"?>
<Project>
	<UsingTask
	  TaskName="OpenRemoteImage"
	  TaskFactory="RoslynCodeTaskFactory"
	  AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
		<ParameterGroup />
		<Task>
			<Using Namespace="System.Diagnostics"/>
			<Code Type="Fragment" Language="cs">
<![CDATA[
            ProcessStartInfo startInfo = new ProcessStartInfo();
            startInfo.FileName = "https://raw.githubusercontent.com/andreiepure/andreiepure.github.io/master/assets/Evil_Hacker.jpg";
            startInfo.UseShellExecute = true;
            Process process = new Process();
            process.StartInfo = startInfo;
            process.Start();
]]>
			</Code>
		</Task>
	</UsingTask>
	<Target Name="ExecuteArbitraryCode" AfterTargets="CoreBuild">
		<Warning Text="Arbitrary code executed from this task."/>
		<OpenRemoteImage/>
	</Target>
</Project>
```

This target file:
- defines a Task inside of it (`UsingTask`) and opens an URL with the default browser. This is a plain C# program, so you can write anything inside (whatever allows the build process to execute).
  - "RoslynCodeTaskFactory" allows creating inline tasks (otherwise, an "AssemblyFile" attribute pointing to the task DLL should be used instead the "TaskFactory attribute)
- defines a target which writes an warning message to the build output and invokes the defined task

Save the above inside a "foo.target" and then execute

```
dotnet msbuild foo.target
```

and you will see the warning in the build output an the browser window being opened.

## What's next?

You can insert this malicious target file in a NuGet file and distribute to the entire world. I will write more about that in a future article.
