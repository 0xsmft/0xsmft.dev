# *.Dist.cs

A distribution target file (*.Dist.cs) setups build flags for the DIST config only. 

Example file:

```cs
using System;
using System;
using SaturnBuildTool;

public class MyProjectGame : GameDistTarget
{
    public override void Init()
    {
        base.Init();

        Name = "MyProjectGame";
        Modules.Add( "MyProject" );
    }
}
```
