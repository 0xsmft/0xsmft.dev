# Release Notes

### 0.2.6

*27 July 2026, 0922 hrs*

Standard alpha release.

Hot reloading works again, console commands, SMAA, GTAO, prefab rework.

- Hot reloading
- Console commands
- CB: Show item location for search results
- Zip Project from editor
- Memory debug stats
- Improve timeline in SkeletalAnimAV
- Agent Debug during runtime
- SMAA
- Prefab2
- GTAO
- Bone Attachments

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.6)

### 0.2.5

*27 May 2026, 0834 hrs*

Standard alpha release.

Sacked PhysX and use JoltPhysics now.

- Standard alpha build.
- Online System (Steam API)
- Jolt Physics
- Selection Outline + jumpflooding
- Worldspace text rendering
- Node Editor Rework
- Replace asset when deleting an asset
- Find Nodes in node editor (Ctrl+F)
- Bloom
- SSAO
- Fix issue with Skeletal Mesh material data
- Texture Streaming
- Content Browser file moving improvements

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.5)

### 0.2.4

*27 March 2026, 1508 hrs*

Standard alpha release.

Fix heap issues, introduce Alura, workflow testing.

- Skeletal Animation, rendering shadows
- Alura UI system, basic UI elements and text rendering
- Show/Hide entites
- Phys: Shape Triggers
- Phys: Character Movement Component
- Camera Preview
- Workflow testing (2025/26) + lots of small workflow changes and bug fixes
- Fix gizmo transformation bug
- Fix heap issues between the Game and the Editor
- Add TextureSourceAssets
- Add billboard component (was already in the engine since Jan 2024 but I never implemented them fully for some reason)
- Fix material issue for the MeshAssetViewers (Static and Skeletal)
- Entity Selection Manager is now multi-selection and multi-context
- Click to select billboards
- Pause RT
- Fix PhysColliders selection debug
- Fix SClass memory leak
- Fix assets with raw files e.g. static meshes needing a .gltf file, not being deleting when the asset was being deleted

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.4)

### 0.2.3

*1 Jan 2026, 0000 hrs*

Standard alpha release.

Skeletal Animation, click to select, Animation Graphs.

- Skeletal Animation, basic playing/animation graph, animation compression
- Animation Graphs
- Improve Mesh importation UI
- Weak Refs
- Non Intrusive ref counting
- Global EntitySelectionManager class
- Destroying Entities during runtime fixes
- Improve event system, add global way to fire events
- Add sub-graphs for Node Editors
- New Task API for Node Editors
- Scene Travelling, initial
- Display Project name in the Title bar
- Full screen viewport
- Multiple Renderer2Ds
- CB Thumbnails for Skeletal Meshes
- Fix show or hide crash
- Mouse Click to select entities from Viewport

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.3)

### 0.2.2

*27 July 2025, 1822 hrs*

Standard alpha release.

Behaviour Trees, SClass rework.

- AI Behaviour Trees, Tasks, Blackboard and Memory (WIP on conditions)
- Better SClasses
- Mouse picking
- Auto saves
- Allow Scene to reject runtime requests
- Add comment Node for NodeEditors
- Various other minor fixes

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.2)

### 0.2.1

*27 May 2025, 2219 hrs*

Standard alpha release.

Content browser thumbnails (ext.), frustum culling, navmesh generation.

- CB Thumbnails
- Undo/Redo
- Quick Actions for CB
- Initial nav mesh
- Frustum Culling
- Reworked Uniform buffers
- Fix ImGui viewport issue (windows lower in the z-order could receive mouse events)

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.1)

### 0.2.0

*27 March 2025, 1602 hrs*

Standard alpha release.

Dist fixes, Audio system fixes, more build tool options.

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

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.0)

### 0.1.4

*1 Jan 2025, 0012 hrs*

Standard alpha release.

SProperties, hot reloading.

- SProperty
- Set Properties from editor exposed from C++
- Hot Reloading
- Add support for XBUTTONS on mouse (Mouse3, Mouse4 etc)
- Various bug fixes
- Add external C++ header tool
- Faster build tool
- Saturn Build Tool Version 0.0.3
- Better PlayerInputController

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.1.4)

### 0.1.3

*27 Sept 2024, 1516 hrs*

Standard alpha release.

- Copy Component button in Scene Hierarchy Panel
- Allow sounds to be modified when runtime active
- Removed Editor Assets
- Add Unicode Support to Ruby (Unicode typing, pasting etc)
- Workflow Fixes (Project browser → distribution)
- Auto adjust for box colliders
- Added “Unsaved changes” modal to scenes
- Added button to find start-up scene, default material and default physics material
- Added options to show or hide the Content Browser Panel and/or Scene Hierarchy Panel

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.1.3)

### 0.1.2

*27 July 2024, 2007 hrs*

Standard alpha release.

- Faster AssetBundle building and reading
- Fix slow LightCulling shader
- Fix StaticMeshes UBs being uploaded every time we want to render one submesh
- FPS Fixes
- Fix project browser thread having high CPU usage
- Fix BuildTool not defining core defines (SAT_DEBUG, SAT_RELEASE, SAT_DIST, UNICODE, _UNICODE, SAT_PLATFORM_WINDOWS)
- Complete Node Editor rework
- Add GraphSounds (Sound blueprint editor)
- Add Node Editor Output Window
- Improve Material Node Editor

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.1.2)

### 0.1.1

*27 May 2024, 0820 hrs*

Standard alpha release.

- Debug Lines
- Shader Hot Reloading
- Content Brower Search
- Message Box in editor
- SAT_CORE_VERIFY
- Flash Attention in Ruby
- Audio System (2D Sounds and preliminary 3D sounds)
- Screenshots

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.1.1)

### 0.1.0

*27 March 2024, 1603 hrs*

Standard alpha release.

Inital alpha release.

Tag link [here](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.0.1)
