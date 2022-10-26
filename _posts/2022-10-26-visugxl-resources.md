---
title:  "VisugXL Belgium 2022 Resources"
---

You've probably arrived on this page after watching my talk _"How to attack a .NET software supply chain"_ at the [VisugXL](https://www.visug.be/Events/80) conference on the 28th of October 2022 (held in Hasselt, Belgium).

Whether you enjoyed or not my talk, please fill in this [anonymous feedback form](https://forms.gle/aBVGdH1CnCjCQh6K6).

As a reminder, these are the three easy steps to do in order to secure you NuGet supply chain against typosquatting and dependency confusion supply chain attacks:

1. Use [Package Source Mapping](https://docs.microsoft.com/en-us/nuget/consume-packages/package-source-mapping).
2. Use `<trusted signers>`: [Manage package trust boundaries](https://docs.microsoft.com/en-us/nuget/consume-packages/installing-signed-packages).
3. Reserve prefixes for both your public and private packages on nuget.org: [Package ID prefix reservation](https://docs.microsoft.com/en-us/nuget/nuget-org/id-prefix-reservation).

In addition, to have the overview of all your direct and transitive dependencies and be aware of changes in your dependency graph [use a NuGet lock file](https://devblogs.microsoft.com/nuget/enable-repeatable-package-restores-using-a-lock-file/).

Some real life NuGet configurations:
- [sonar .NET analyzers](https://github.com/SonarSource/sonar-dotnet/blob/8.47.0.55603/analyzers/NuGet.Config) (and check also one of the [lock files](https://github.com/SonarSource/sonar-dotnet/blob/8.47.0.55603/analyzers/src/SonarAnalyzer.CSharp/packages.lock.json))
- [Sonar Scanner for .NET](https://github.com/SonarSource/sonar-scanner-msbuild/blob/5.8.0.52797/NuGet.Config)
- [NuGetGallery](https://github.com/NuGet/NuGetGallery/blob/v2022.10.19/NuGet.config)

The source code for my demos [is on GitHub](https://github.com/andreiepure/DependencyConfusionDemo), feel free to use it when explaining these problems to your colleagues.

For more docs from Microsoft and more resources on software supply chain attacks, read  the second part of [this post](https://andreiepure.ro/2022/08/28/dotnetday-resources.html).

Last, but not least: [we're hiring at Sonar](https://www.sonarsource.com/company/careers/)! 
