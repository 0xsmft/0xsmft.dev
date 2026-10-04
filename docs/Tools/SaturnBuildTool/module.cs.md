# *.Module.cs

A Module file (*.Module.cs) defines constant build configuration data that is to be used accross all configurations.

For example a Module.cs file may set up the IncludeDirs, SourceDirs and how the source files should be found.

It may also be used setup PCH information.

Example file:

```cs
using System;
using System.IO;

using SaturnBuildTool;

public class MyProjectModule : GameModule
{
    public override void Init()
    {
        base.Init();

        // Add our source dir as an include.
        Includes.Add( "Source/MyProject" );

        // Add our source dir.
        SourcePaths.Add( "Source/MyProject" );

        SourceDirectoryOptions = SourceDirectoryOptions.Custom;
        OutputDirectoryOptions = OutputDirectoryOptions.UseTargetDirectory;
    }
}
```
