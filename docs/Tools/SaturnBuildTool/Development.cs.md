# *.Development.cs

A development target file (*.Dist.cs) setups build flags for the DEBUG-ASAN, DEBUG and RELEASE config only. 

Example file:

```cs
using System;
using SaturnBuildTool;

public class MyProjectEditor : GameDevelopmentTarget
{
    public override void Init()
    {
        base.Init();

        Name = "MyProject";

        Modules.AddRange( new string[] {
            "MyProject"
        } );

        Includes.Add( "MyProject/Source/MyProject" );
    }
}
```
