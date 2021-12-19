In my experience, code coverage tooling seems to be better for Java than for C#, even if there's a huge company behind .NET.

For Java, JaCoCo just works and IntelliJ Community IDEA has integrated code coverage with branch coverage.

For C# and Visual Studio, this are not that simple and out-of-the-box.

First of all, Visual Studio Community doesn't have code coverage integrated. That's rather weird.

Second, when using the ultra-expensive Visual Studio Enterprise, code coverage tooling exists based on VSCoverage, however its branch coverage is rather limited. It tells if a line is partially covered by tests, however it doesn't give details about how badly covered it is. There's quite a big difference between 1/10 conditions and 9/10 conditions being covered. And the powerful syntax of C# allows for complex one-liners with many conditions, so branch coverage is quite needed for ensuring good code quality.

When parsing the VS Coverage coverage reports for SonarQube and SonarCloud, we cannot extract information about the branch coverage.

The .NET IntelliJ code coverage tool, dotCover, isn't brighter either. It's even worse: it doesn't support branch coverage at all, and there's a community post on it.

Thankfully, OpenCover has been a very nice tool with supported branch coverage. The only downside is that it was working only with .NET Framework, so it's Windows dependant. And this year its author announced (rather abrupty) the end of life of the project.

And then there's coverlet, which has branch coverage support, is cross-platform and is a .NET Foundation project. I imagine that VS Coverage won't be developed further to support branch coverage given that coverlet is there.

There's also ..., recommended by the OpenCover author, however I don't have experience with it, I'll be glad to hear your thoughts on it.