---
title:  "MSBuild vocabulary"
---

# The MSBuild scripting language

MSBuild is the Microsoft Build Engine. What might be less known is that it offers a scripting language. An MSBuild file is usually a script, orchestrating what happens during the build process.

## Concepts

The MSBuild scripting language concepts:
- *properties* are variables; some [are reserved](https://learn.microsoft.com/en-us/visualstudio/msbuild/common-msbuild-project-properties); some are [predefined by MSBuild](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-reserved-and-well-known-properties) during the build process; others are environment variables; and others are customized in MSBuild projects and props files
- *items* are [inputs in the build system](https://learn.microsoft.com/en-us/visualstudio/msbuild/common-msbuild-project-items), usually files - these are used to include or exclude files from the build process; each item has [some metadata](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-well-known-item-metadata) attached to it
- *tasks* are atomic build operations, like "compile" or "copy file"; there are plenty [built-in tasks](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-task-reference), and you can define your own by extending [`Microsoft.Build.Utilities.Task`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.build.utilities.task); a task must be present inside a target in order to be executed
- *targets* are groups of tasks to be executed together; they enable sections of the build process to be called from the command line with the `-target:` [switch](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-command-line-reference)
  - targets can have attributes that specify the order of operations (`InitialTargets`; `DependsOnTarget`; `BeforeTarget`) - MSBuild uses this information to build a Direct Acyclic Graph of targets to execute
  - each target runs **only once** in a single build

## Convention

MSBuild offers an XML scripting language. By convention, MSBuild files have a limited set of extensions. However, it is only a convention - any of the below files (or a simple `.xml` file) can hold the definition of MSBuild properties, tasks and targets. That being said, by convention there are three types of files:
- project files (`.csproj`, `.vbproj`, `.esproj` etc)
- target files (`.target`)
  - The `Microsoft.NET.Sdk` target file is referenced in .NET csproj files (`<Project Sdk="Microsoft.NET.Sdk">`)
  - The `Directory.Build.target` file is picked up by MSBuild as a customization file in the folder structure of your project
- property files (`.props`)
  - The `Directory.Build.props` file can hold build config and is picked up by MSBuild

Tasks are normally kept in libraries (DLLs) which are referenced by other files.
MSBuild files can import other MSBuild files. Usually *target* files reference other *target* files.

Microsoft offers very good documentation each of these [MSBuild concepts](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-concepts).

# Hello World script

Create a file, name it "hello.txt" and paste the content below.

```
<?xml version="1.0" encoding="utf-8"?>
<Project>
	<Target Name="ExecuteArbitraryCode" AfterTargets="CoreBuild">
		<Warning Text="Hello, World!"/>
	</Target>
</Project>
```

To execute it, run

```
dotnet msbuild hello.txt --verbosity:quiet
```
It will output

> MSBuild version 17.4.0+18d5aef85 for .NET
C:\blog\playground\hello.txt(4,3): warning : Hello, World!

Congratulations! You wrote your first MSBuild script.
