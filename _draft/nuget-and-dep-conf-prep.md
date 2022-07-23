# NuGet and Dependency Confusion

Copyright: Andrei Epure. All rights reserved.
If you get inspired by this draft, please mention it as a source.

Preparing for giving the session "Dependency confusion and its cure. A NuGet story." at .NET Day Switzerland 2022 (https://dotnetday.ch/speakers/andrei-epure.html).

## Structure

Initial draft for the talk structure:


0. Warm-up - questions for the public (3 minutes)
  * who uses NuGet, who changed a config file, who knows what version of NuGet they use, who uses NuGet 6
  * who knows what dependency confusion attack is

1. Brief recap of how NuGet traditional configuration (5 minutes)
  * pre NuGet 6
  * introduce vocabulary
  * describe structure of the session
  
2. High level explanation of the attack (10 minutes)
  * mention behavior for Python and NuGet
  
3. NuGet Demo (5 minutes)
  * demonstrate the behavior from the high level explanation
  * hybrid configuration
  * keep it simple - either local repo or Azure DevOps repo
  * don't focus on managing to make the public calls faster than the private calls - the is a bonus after the rest of the presentation is done
  * possible demos (but not enough time)
    * different versions, same name - this can be done with a local feed - wildcard version in csproj; show public version; have a local package with a greater version
	* say that you pin your version - pray that your private feed will be the fastest and there's no malicious package on the public feed with the same version _(might be slightly overkill to demo, might leave it just as a mention, linking to the history)_

4. Explain history (5 minutes)
  * show the GitHub issue discussion around the behavior
  * show timeline of change (after Alex Birsan's article)

5. How to protect yourself (15 minutes)
  * _"Do you feel lucky, or do you want to make the life of an attacker more difficult? It doesn't cost much to add safety nets in your supply chain, it's easy and straight forward"_.
  * explain all safety nets, pre-NuGet 6 and post-NuGet 6
  * pre-NuGet 6 : owner filtering, repo signature, package owner signature where possible, fixed versions, package.lock.json + verify checksums  
    * _"It can be tedious to add a list of the owners of all your dependencies, however- are you willing to accept packages from other owners?"_
  * post-NuGet 6: domains
  
6. How to protect your users (5 minutes)
  * reserve prefix - explain process, show behavior, show email thread
  * sign packages to allow signature verification
  * _"if the third party open source you use don't have reserved prefixes on nuget.org, ask them to reserve them!"_
  * _"ask nuget.org to reserve the prefixes of your private packages - better safe than sorry"_
  * _"let's strengthen the ecosystem!"_
  
7. Conclusions
  * _"Be aware of what can go wrong. Be aware of your supply chain. Be aware of the risks your code and dependencies have"._

8. Q & A (? minutes)


## Preparation

### NuGet 101

https://aka.ms/Nuget101

nice intro info from video 1/5

Simple definitions
- .NET dev platform = languages + libraries
- Package = compiled libraries + descriptive metadata
- NuGet = the system to manage libraries in the ecosystem

NuGet.org 
- numbers of packages
- Package - shows if it is verified

### Microsoft docs

GH docs: https://github.com/NuGet/docs.microsoft.com-nuget
Version: commit 53f580b29

#### General

1. https://docs.microsoft.com/en-us/nuget/what-is-nuget

What I can use:  
- // Overall, not much (don't care about package targeting; nuget tools)
- "The flow of packages between creators, hosts, and consumers" - the image can serve as a reminder of how it works and that there can be private hosts
- "Managing dependencies" 
  - the image can help as a reminder of the complexity of dependency management
  - also, the mention that a package can appear multiple times with multiple versions is worthwhile
- "Tracking references and restoring packages" - probably I won't talk about _package management formats_ (PackageReference vs packages.config) because of lack of time
- "What else does NuGet do?"
  - _"To avoid bringing multiple versions of that package into the application itself, NuGet sorts out which single version can be used by all consumers."_
  - mentions "version ranges" -


#### Concepts

2. Package installation process https://docs.microsoft.com/en-us/nuget/concepts/package-installation-process

The steps that happen during resolution:
  - verify in the local cache (global-packages folder)
  - if not, download it from the sources specified in the configuration files. Package Source Mapping (NuGet 6+) get applied here.
  - the order of sources:
    - FIRST: local folders and network drives.
    - SECOND: HTTP online sources. 
  - for HTTP online sources, attempt to use the HTTP cache (expiring in 30 minutes).
    - If hit, CACHE appears in the log.
    - if the package is specified using a floating version, _ALL_ sources are contacted to figure out the best match.
    - if the HTTP cache is not hit, NuGet attempts to download from all the sources listed in the config. "GET" and "OK" appear in the output.
    - if the package is not acquired successfully, NU1103 (with the last checked source, even if all sources have been checked).

After downloading the package:
- save the package in the hhtp-cache
- install in the per-user global-packages folder - a subfolder for each package identifier, then subfolders for each installed version of the package
- then NuGet installs package dependencies as required. It might update package versions in the process.

Update project files and folders:
- for PackageReference, updates the dependency graph stored in obj/project.assets.json
- Update app.config and/or web.config if the package uses source and config file transformations (see _Transforming source code and configuration files_ below)


3. Package versioning https://docs.microsoft.com/en-us/nuget/concepts/package-versioning

Version basics
- Major.Minor.Patch[-Suffix]

Pre-release versions
- any string as a suffix to denote a pre-release version (NuGet treats as string)
- convention: `-alpha` (WIP), `-beta` (can have bugs), `-rc` (stable)

Version ranges
- 1.0 - **minimum** version, inclusive (thus if patch version is missing, it's a version rage)
- (1.0,) - min version, exclusive
- [1.0] - exact version match
- (,1.0] - max version, inclusive
- (,1.0) - max version, exclusive
- [1.0,2.0] - exact range, inclusive
- (1.0,2.0) - exact range, exclusive
- [1.0,2.0) - mixed inclusiv minimum and exclusive maximum

> **!!** Version ranges in PackageReference **include pre-release versions.**

PackageReference floating version
- floating notation, `*`, for Major, Minor, Patch, and pre-release suffix parts of the number. 

> By design, floating versions do not resolve prerelease versions unless opted into.

> When resolving package references and multiple package versions differ **only by suffix**, NuGet chooses **a version without a suffix first**, then applies precedence to pre-release versions in **reverse alphabetical order**.

Examples

> Without a version or version range, NuGet 2.8.x and earlier chooses the latest available package version when resolving a dependency, whereas NuGet 3.x and later chooses the lowest package version. Specifying a version or version range avoids this uncertainty.

In [these examples](https://docs.microsoft.com/en-us/nuget/concepts/package-versioning#references-in-project-files-packagereference)
- Version="6.1" - Will resolve to the smallest acceptable stable version
- Version="6.*" - highest stable

Floating version resolutions
- `1.1.*-*` needs to be used to accept the highest, including pre-release

> Floating version resolution does not take into account whether or not a package is listed. Floating version resolution will be resolved locally if the conditions can be satisfied with packages in the Global Package Folder.

Normalized version numbers
- Leading zeroes are removed from version numbers
  - 1.00 is treated as 1.0
  - 1.01.1 is treated as 1.1.1
  - 1.00.0.1 is treated as 1.0.0.1
- A zero in the fourth part of the version number will be omitted
  - 1.0.0.0 is treated as 1.0.0
  - 1.0.01.0 is treated as 1.0.1
- SemVer 2.0.0 build metadata is removed
  - 1.0.7+r3456 is treated as 1.0.7

4. Dependency resolution https://docs.microsoft.com/en-us/nuget/concepts/dependency-resolution

5. Best practices (🍞+🧈) https://docs.microsoft.com/en-us/nuget/concepts/security-best-practices

6. .props and .targets in a package (🐱‍👤) https://docs.microsoft.com/en-us/nuget/concepts/msbuild-props-and-targets

#### Consume packages

7. 

#### Create packages

- see best practices here as well

##### [Transforming source code and configuration files](https://docs.microsoft.com/en-us/nuget/create-packages/source-and-config-file-transformations) 

Specifying config file transformations
- Include `app.config.transform` and `web.config.transform` files in your package's content folder, where the `.transform` extension tells NuGet that these files contain the XML to merge with existing config files when the package is installed. When a package is uninstalled, that same XML is removed.
- Include `app.config.install.xdt` and `web.config.install.xdt` files in your package's content folder, using XDT syntax to describe the desired changes. With this option you can also include a `.uninstall.xdt` file to reverse changes when the package is removed from a project.

XML transforms
- As a more extensive example, the [Error Logging Modules and Handlers for ASP.NET (ELMAH)](https://www.nuget.org/packages/elmah/) package adds many entries into web.config, which are again removed when a package is uninstalled.
  - To examine its web.config.transform file, download the ELMAH package from the link above, change the package extension from .nupkg to .zip, and then open content\web.config.transform in that ZIP file.

XDT transforms
- to make XDT transforms work withPackageReference, refer to [this sample](https://github.com/NuGet/Samples/tree/main/XDTransformExample)
- You can modify config files using XDT syntax. You can also have NuGet replace tokens with project properties by including the property name within $ delimiters (case-insensitive).


#### Publish packages

##### Publish to a private feed

Create your own NuGet.Server: https://docs.microsoft.com/en-us/nuget/hosting-packages/nuget-server

#### References

##### NuGet Server API 

https://docs.microsoft.com/en-us/nuget/api/overview

(idea : if rate limit is met on private server, then the public server will get priority)

#### Resources

##### Release notes

- track the vulnerabilities throughout versions, create a small history of this

### Contributor blog post

https://dev.to/loicsharma/the-nuget-protocol-4m8h

Short overview of the protocol. Doesn't seem to bring useful info for the talk...