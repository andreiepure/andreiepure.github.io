---
title:  ".NET Day Switzerland 2022 Resources"
---

You probably arrived on this page after watching [my talk about Dependency Confusion](https://dotnetday.ch/speakers/andrei-epure.html) at DotNetDay Switzerland on the 30th of August 2022.

As a reminder, these are the three easy steps to do in order to secure you NuGet supply chain against dependency confusion attacks (links to Microsoft docs):

1. Use [Package Source Mapping](https://docs.microsoft.com/en-us/nuget/consume-packages/package-source-mapping)
2. Use `<trusted signers>`: [Manage package trust boundaries](https://docs.microsoft.com/en-us/nuget/consume-packages/installing-signed-packages)
3. Reserve prefixes for both your public and private packages on nuget.org: [Package ID prefix reservation](https://docs.microsoft.com/en-us/nuget/nuget-org/id-prefix-reservation)

The source code for my demos [is on GitHub](https://github.com/andreiepure/DependencyConfusionDemo), feel free to use it when explaining the problem to your colleagues.

More advice from Microsoft:
- [NuGet Best practices for a secure software supply chain](https://docs.microsoft.com/en-us/nuget/concepts/security-best-practices)
- Advice for more tech stacks (Maven, Gradle, NuGet, npm, Pip, Yarn): [3 Ways to Mitigate Risk When Using Private Package Feeds](https://azure.microsoft.com/en-us/resources/3-ways-to-mitigate-risk-using-private-package-feeds/)

You can read about the NuGet historical design decision of having a non-deterministic package resolution behavior for hybrid configurations (fetching packages from all configured sources in parallel): [NuGet/Home#5611](
https://github.com/NuGet/Home/issues/5611).

About substitution attacks - the original article by security researcher Alex Bîrsan from Romania: [Dependency Confusion: How I Hacked Into Apple, Microsoft, and Dozens of Other Companies](https://medium.com/@alex.birsan/dependency-confusion-4a5d60fec610).

About typosquatting:
- [Typosquatting programming language package managers (2016)](https://incolumitas.com/2016/06/08/typosquatting-package-managers/) in the NPM, PyPi and rubygems ecosystems
- [IconBurst NPM software supply chain attack grabs data from apps and websites (2022)](https://blog.reversinglabs.com/blog/iconburst-npm-software-supply-chain-attack-grabs-data-from-apps-websites) in the NPM ecosystem

About the SolarWinds breach:
- overview, timeline: [New Findings From Our Investigation of SUNBURST](https://orangematter.solarwinds.com/2021/01/11/new-findings-from-our-investigation-of-sunburst/)
- technical explanation of SUNSPOT, the malicious tool that was deployed into the SolarWinds build environment: [SUNSPOT: An Implant in the Build Process.](https://www.crowdstrike.com/blog/sunspot-malware-technical-analysis/)
- technical explanation of SUNBURST, the trojan shipped inside Orion: [Highly Evasive Attacker Leverages SolarWinds Supply Chain to Compromise Multiple Global Victims With SUNBURST Backdoor](https://www.mandiant.com/resources/blog/evasive-attacker-leverages-solarwinds-supply-chain-compromises-with-sunburst-backdoor)

Whether you enjoyed or not my talk, please fill in this feedback form (Google Forms, anonymous): https://forms.gle/t5JVPzQLUWQGy1vF9.

Last, but not least: [we're hiring at Sonar](https://www.sonarsource.com/company/careers/)! 
