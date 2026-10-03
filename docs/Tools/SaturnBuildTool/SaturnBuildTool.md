# SaturnBuildTool

`SaturnBuildTool` is a custom build tool that compiles Saturn game projects (.sprojects) into a final binary.

The build tool can support a variety of different compilers.

| Toolchain | Supported |
| ---------- | ---------- |
| MSVC | Yes, x64 only
| Clang | Yes, x64 only
| AppleClang | Yes, AArch only
| GCC | Yes, x64 only

The latest version of SaturnBuildTool is 5.1

## Command line options

For an example, this is the required arguments to build a project.

Windows:
`SaturnBuildTool.exe /BUILD /WIN64 /PROJECT:{path_to_prj_root} /NAME:MyProject /DEBUG`

macOS:
`SaturnBuildTool /BUILD /APPLE /PROJECT:{path_to_prj_root} /NAME:MyProject /DEBUG`

### Full list

#### Action Options
/BUILD*          -- build the project

/REBUILD*        -- rebuild the project, ignoring the FileCache and TaskCache

/CLEAN*          -- clean the project

#### Projects Options
/PROJECT*        -- path to the project root dir (same place where the .sproject file is located)

/NAME*           -- project name MUST match with the .sproject file name!

/SATURNDIR       -- override the Saturn Root Directory by default the build tool will use the "SATURN_DIR" environment variable

/SRC             -- override the Source Dir, by default its "Source/{prj.name}", when overriding make sure the path is relative to the .sproject path

#### Compile Options
##### Platform Options
/WIN64*          -- build for Windows x64

/LINUX64*        -- build for Linux x64

/APPLE*          -- build for macOS AArch64 (Apple Silicon)

##### General
/CC              -- specify toolchain to use. On Windows by default this is set to MSVC, on linux and macOS this is set to CLANG. Options are /CC={MSVC|GCC|CLANG}

/HOTRELOAD       -- this is an internal command and is used for hot reloading, when this command is suggested the build tool will create a special timestamp file and output files with the timestamp suffix

/DISTASDBG       -- Build for Dist but compile with debug symbols and no optimisation. However, /DIST must be suggested

##### Configuration Options
/DEBUG*         -- build the project for Debug configuration with full symbols

/RELEASE*       -- build the project for Release configuration with symbols on for this project but symbols off for third party projects

/DIST*          -- build the project for the Dist configuration

##### Warning Options
/XW+            -- treat warnings as errors

/XW-            -- no warnings

/XW1            -- warnings level one

/XW2            -- warnings level two

/XW3            -- warnings level three (default)

/XW4            -- warnings level four

/XWAx           -- all warnings

### Auxiliary Options
/HELP            -- this command that displays the help message

/INCLUDESTREE    -- displays and create an include tree

/VERISON         -- displays the version for the build tool

/ARGS+           -- displays the compiler and linker command line arguments

/EXPORTFILECACHE -- exports the FileCache into a human readable format

/EXPORTTASKCACHE -- exports the TaskCache into a human readable format

/SHOWARGS        -- show the command line arguments for the BuildTool

"*" indicates a required argument.
