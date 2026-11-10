---
date: 2026-03-27
categories:
  - Saturn
  - News
authors:
  - 0xsmft
slug: saturn_engine_alpha_0_2_4
description: >
    Standard Alpha release 0.2.4
---

# Saturn Engine Alpha 0.2.4 Released 🎉

Last Updated: 27 March 2026

Today, I have released an update for Saturn.

Changes:
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


The build is not available to downloaded but you can build it from source using [this link](https://github.com/0xsmft/Saturn-Engine/releases/tag/alpha-0.2.4).

-smft

*27 March 2026, 1508 hrs*
