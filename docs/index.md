# Saturn Engine

Saturn is primarily an early-stage cross-platform 3D game engine.

<p>
    <a href="https://github.com/BEASTSM96/Saturn-Engine/blob/vulkan/LICENSE"><img alt="License" src="https://img.shields.io/badge/license-MIT-green.svg"></a>
    <a href="https://img.shields.io/github/repo-size/BEASTSM96/Saturn-Engine"><img alt="Repo Size" src="https://img.shields.io/github/repo-size/BEASTSM96/Saturn-Engine"></a>
    <a href="https://trello.com/b/baqP3fvB/saturn-engine"><img alt="Trello" src="https://img.shields.io/badge/Trello-saturn--engine-blue"></a>
</p>

Saturn supports the following platforms listed below:

| Platform | Supported | Architecture | Build Status | Stability |
| -------- | --------- | ------------ | ------------ | --------- |
| Windows 10+ | ✅ | x86_64 & AArch64 |     <a href="https://github.com/BEASTSM96/Saturn-Engine/actions/workflows/Windows.yml"><img alt="Repo Size" src="https://github.com/BEASTSM96/Saturn-Engine/actions/workflows/Windows.yml/badge.svg"></a> | Very stable
| Linux | 🕗 *[Progress](https://trello.com/c/o43wueQO/9-preliminary-linux-support)* | x86_64 | No CI yet. | N/A
| macOS 15+ (Sequoia) | ✅ | AArch64 (Apple M-Series) | <a href="https://github.com/BEASTSM96/Saturn-Engine/actions/workflows/MacOS-Arm.yml"><img alt="macOS CI" src="https://github.com/BEASTSM96/Saturn-Engine/actions/workflows/MacOS-Arm.yml/badge.svg"></a> | Unstable

!!! info "Please read the following information"

    Windows ARM builds are only available on Windows 11.

For information on building the engine please visit the [README](https://github.com/0xsmft/Saturn-Engine/blob/vulkan/README.md).

<div class="grid cards" markdown>

-   __Game Framework__

    ---

    The GameFramework module is the main module for gameplay.

    [:octicons-arrow-right-24: Character](Game%20Framework/character.md)

    [:octicons-arrow-right-24: SClass](Game%20Framework/sclass.md)

    [:octicons-arrow-right-24: SObject](Game%20Framework/sobject.md)

-   __Scene__

    ---

    For all documentation about the ECS and the Scene system.

    [:octicons-arrow-right-24: Entity](Scene/entity.md)

    [:octicons-arrow-right-24: Components](Scene/components.md)

-   __Alura__

    ---

    For all documentation about Alura, the in-game UI system.

    [:octicons-arrow-right-24: AluraMainPage](Alura/alura.md)

    [:octicons-arrow-right-24: AluraCanvas](Alura/aluracanvas.md)

    [:octicons-arrow-right-24: AluraColour](Alura/aluracolour.md)

    [:octicons-arrow-right-24: AluraStylingProfile](Alura/alurastylingprofile.md)

-   __Physics__

    ---

    For all documentation about the Physics system.

    [:octicons-arrow-right-24: Rigidbody](Physics/physicsrigidbody.md)

-   __Foundation__

    ---

    For all documentation about the lower level classes and the core foundation of the engine.

    [:octicons-arrow-right-24: Passkey](Foundation/passkey.md)

    [:octicons-arrow-right-24: Random](Foundation/random.md)

    [:octicons-arrow-right-24: Ref](Foundation/ref.md)

    [:octicons-arrow-right-24: SharedPtr](Foundation/sharedptr.md)


-   __Asset__

    ---

    For all documentation about the Asset system.

    [:octicons-arrow-right-24: Asset](Asset/asset.md)

    [:octicons-arrow-right-24: AssetManager](Asset/assetmanager.md)

    [:octicons-arrow-right-24: AssetRegistry](Asset/assetregistry.md)
    

</div>
