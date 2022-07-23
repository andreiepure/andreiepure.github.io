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

### Microsoft docs

#### General

1. https://docs.microsoft.com/en-us/nuget/what-is-nuget

What I can use:  
- not much (don't care about package targeting; nuget tools)
- the image in "The flow of packages between creators, hosts, and consumers" as a reminder of how it works and that there can be private hosts
- the image in "Managing dependencies" can help as a reminder of the complexity of dependency management; also, the mention that a package can appear multiple times with multiple versions is worthwhile;

#### Concepts

2. Package installation process https://docs.microsoft.com/en-us/nuget/concepts/package-installation-process

3. Package versioning https://docs.microsoft.com/en-us/nuget/concepts/package-versioning

4. Dependency resolution https://docs.microsoft.com/en-us/nuget/concepts/dependency-resolution

5. Best practices (🍞+🧈) https://docs.microsoft.com/en-us/nuget/concepts/security-best-practices

6. .props and .targets in a package (🐱‍👤) https://docs.microsoft.com/en-us/nuget/concepts/msbuild-props-and-targets

#### Consume packages

7. 

#### Create packages

- see best practices here as well

#### References

##### NuGet Server API

#### Resources

##### Release notes

- track the vulnerabilities throughout versions, create a small history of this
