---
title:  "How to secure your NuGet supply chain"
---

You've probably arrived on this page after watching my talk _"How to attack a .NET software supply chain"_ at the [VisugXL](https://www.visug.be/Events/80) conference (October 2022 in Hasselt, Belgium), also presented under the name "How your .NET software supply chain is open to attack : and how to fix it" at Techorama Belgium (May 2023), Techorama Netherlands (October 2023) and WeAreDevelopers Berlin (July 2024).

As a reminder, these are the easy steps to do in order to secure you NuGet supply chain against typosquatting and dependency confusion supply chain attacks:

1. Use `<clear />` to avoid inheriting the system configuration (because of [how settings are applied in NuGet](https://learn.microsoft.com/en-us/nuget/consume-packages/configuring-nuget-behavior#how-settings-are-applied)). By using `<clear />`, you ensure the NuGet resolution of your builds are fully deterministic and repeatable.
2. Use [Package Source Mapping](https://docs.microsoft.com/en-us/nuget/consume-packages/package-source-mapping) if you have a hybrid (private and public) configuration, to be protected against dependency confusion attacks. You can use the [NuGet.PackageSourceMapper](https://www.nuget.org/packages/NuGet.PackageSourceMapper#readme-body-tab) tool to help you generate the configuration for your repository. Alternatively, instead of using multiple package sources, configure only a single package source and control which packages you mirror from the public source in your private source.
3. Use `<trusted signers>`: see [Manage package trust boundaries](https://docs.microsoft.com/en-us/nuget/consume-packages/installing-signed-packages). You can use trusted signers for both signed packages (when you will provide the certificate hash), and for unsigned packages (by simply providing the name of the account that published the package you trust). This will help defend your project against unwanted typosquatting attacks.
4. Reserve prefixes for both your public and private packages on nuget.org: [Package ID prefix reservation](https://docs.microsoft.com/en-us/nuget/nuget-org/id-prefix-reservation). It is important to reserve the prefixes for your private packages so that malicious users won't publish public packages with those names, to attempt dependency confusion attacks. Reserving prefixes for public packages also reduces the surface attack of typosquatting attacks.

These are my top recommendations. You can find more on Microsoft's [NuGet Security Best Practices](https://learn.microsoft.com/en-us/nuget/concepts/security-best-practices).

In addition, to have the overview of all your direct and transitive dependencies and be aware of changes in your dependency graph [use a NuGet lock file](https://devblogs.microsoft.com/nuget/enable-repeatable-package-restores-using-a-lock-file/).

Some real life NuGet configurations:
- [sonar .NET analyzers](https://github.com/SonarSource/sonar-dotnet/blob/8.47.0.55603/analyzers/NuGet.Config) (and check also one of the [lock files](https://github.com/SonarSource/sonar-dotnet/blob/8.47.0.55603/analyzers/src/SonarAnalyzer.CSharp/packages.lock.json))
- [Sonar Scanner for .NET](https://github.com/SonarSource/sonar-scanner-msbuild/blob/5.8.0.52797/NuGet.Config)
- [NuGetGallery](https://github.com/NuGet/NuGetGallery/blob/v2022.10.19/NuGet.config)

The source code for my demos [is on GitHub](https://github.com/andreiepure/DependencyConfusionDemo), feel free to use it when explaining these problems to your colleagues. In the "slides" folder you can find the Techorama and WeAreDeveloper slides.

For more docs from Microsoft and more resources on software supply chain attacks, read  the second part of [this post](https://andreiepure.ro/2022/08/28/dotnetday-resources.html).

Last, but not least: [we're hiring at Sonar](https://www.sonarsource.com/company/careers/)! 


| Version Date        | Change
| ------------- |:-------------:|
| 2022-10-26      | Initial version |
| 2024-07-15      | Update title, mention other talks, remove 2022 feedback form. Add reference to the NuGet.PackageSourceMapper tool. Mention <clear>. Add more details. |
