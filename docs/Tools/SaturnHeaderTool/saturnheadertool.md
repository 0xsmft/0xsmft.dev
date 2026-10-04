# SaturnHeaderTool

SaturnHeaderTool (SHT) is a command-line application that is responsible for generating reflection code.

The contents that the header tool generates can be found the projects `Build/Generated` folder. The file contents should not be modified.

The header tool only generates code if a class is marked as `SCLASS()`, after that it may generated additional code if a property is marked with `SPROPERTY()`.

In order for the header tool to run it must be given a valid recipe file.

The latest version of the HeaderTool is 0.2.7 (8199), conforming to SBT 5.1 

## Command line arguments

/NOMSG -- disable startup banner message.

/PCH -- path to the PCH header file.

/FC -- path to recipe.

/OUT -- output directory.

/SRC -- source search directory.

/HOTRELOAD -- generate for a hot-reload.

/DEBUG -- generate for debug

/RELEASE -- generate for release

/DIST -- generate for dist
