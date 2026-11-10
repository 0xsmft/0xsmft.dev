---
date: 2025-03-27
categories:
  - Saturn
  - News
authors:
  - 0xsmft
slug: saturn_engine_alpha_0_2_0
description: >
    Standard Alpha release 0.2.0
---

# Saturn Engine Alpha 0.2.0 Released 🎉

Last Updated: 27 March 2025

Today, I have released a major update for Saturn. We are now in the second alpha builds.

Changes:
- Add more mesh import options
- Fix Material Assets being creating every time the editor was launched
- Add Asset Dependencies for Entities and MaterialRegistry
- Node Editor Improvements (primarily code side)
- Sound Node Editor: Add RandomPitch node add SetPitch node
- Add back math nodes to Material node editor
- Add Asset Dependencies for Assets
- Suspend Runtime
- Media Controls in SoundAssetViewer
- New “Delete Asset” modal
- Fix clipboard size being wrong, resulting in crash from Windows when clearing clipboard
- Add Looping to GraphSound
- Add new build tool command line args (/DISTASDBG) (/SHOWINCLUDES) (/SHOWCONSOLE) (/HELP) (/VERSION) (/SATURNDIR) (/ARGS+)
- /SATURNDIR, override default saturn directory path
- /DISTASDBG, will build Dist with C7 pdbs
- /SHOWINCLUDES, will create and output an include tree
- /SHOWCONSOLE, will build the project with a console (Only on Dist), equivalent to /SUBSYSTEM:CONSOLE on Windows
- /ARGS+, show compiler and linker command line args
- Fix Ruby losing mouse capture when child window dragged out from main window, resulting in offset mouse position, mouse released events not firing
- Add CB thumbnail for TextureSourceAssets
- Project thumbnail
- Fix Dist builds relying on .sproject file and EngineSettings config file
- Remove Game Thread

The build is not available to downloaded but you can build it from source using [this link](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.0).

-smft

*27 March 2025, 1602 hrs*
