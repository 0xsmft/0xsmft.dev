# Components

``#include "Saturn/Scene/Components.h"``

Data and behaviour that can added to an [Entity](entity.md).

## All Compoents

### TransformComponent

Entity transformation data.

```cpp
struct TransformComponent
```

#### Public members

```cpp
glm::vec3 Position = { 0.0f , 0.0f, 0.0f };
glm::vec3 Scale	= { 1.0f , 1.0f, 1.0f };
```

#### Public constants

```cpp
static constexpr glm::vec3 Up = { 0.0f, 1.0f, 0.0f };
static constexpr glm::vec3 Right = { 1.0f, 0.0f, 0.0f };
static constexpr glm::vec3 Forward = { 0.0f, 0.0f, -1.0f };
```

#### Public functions

```cpp
glm::mat4 GetTransform() const;

void SetTransform( const glm::mat4& rTransfrom );

// NOTE: Rotation should be specified in euler angles.
void SetPositionRotationScale( const glm::vec3& rPosition, const glm::vec3& rRotation, const glm::vec3& rScale );

// NOTE: Rotation should be specified in quaternion form.
void SetPositionRotationScale( const glm::vec3& rPosition, const glm::quat& rRotation, const glm::vec3& rScale );

// Where rotation is a euler angle.
// Rotational values must be radians.
void SetRotation( const glm::vec3& rotation );

void SetRotationInDeg( const glm::vec3& rotation );

// Rotational values must be radians.
void SetRotation( const glm::quat& rotation );

// Rotational values will be in radians.
glm::quat GetRotation() const;

// Rotational values will be in radians.
glm::vec3 GetRotationEuler() const;
```

#### Private members

```cpp
glm::quat RotationQuat = { 1.0f, 0.0f, 0.0f, 0.0f };
glm::vec3 Rotation = { 0.0f, 0.0f, 0.0f };
```

### TagComponent

Entity Tag data.

```cpp
struct TagComponent
```

#### Public members

```cpp
std::string Tag;
TagComponent( const std::string& rTag );
```

### IdComponent

Unqiue entity ID component.

```cpp
struct IdComponent
```

#### Public members

```cpp
UUID ID;
IdComponent( const UUID& rUUID );
```
### StaticMeshComponent

Data for a static mesh.

```cpp
struct StaticMeshComponent
```

#### Public members

```cpp
MemoryAssetDependency<AssetType::StaticMesh> AssetID;
Ref<Saturn::StaticMesh> Mesh;
Ref<Saturn::MaterialRegistry> MaterialRegistry;

StaticMeshComponent( const Ref<StaticMesh>& rMesh );
```

### SkeletalMeshComponent

Data for a skeletal mesh.

```cpp
struct SkeletalMeshComponent
```

#### Public members

```cpp
MemoryAssetDependency<AssetType::SkeletalMesh> AssetID;

Ref<Saturn::SkeletalMesh> Mesh;
Ref<Saturn::MaterialRegistry> MaterialRegistry;

// Animation
MemoryAssetDependency<AssetType::AnimationController> AnimationControllerAssetID;

// LocalAnimator is only valid for runtime objects
Ref<Animator> LocalAnimator;

AnimatorType AnimatorType = AnimatorType::Single;

SkeletalMeshComponent( const Ref<SkeletalMesh>& rMesh );
```

### DirectionalLightComponent

Data for a single directional light.

```cpp
struct DirectionalLightComponent
```

#### Public members

```cpp
glm::vec3 Radiance = { 1.0f, 1.0f, 1.0f };
float Intensity = 1.0f;
bool CastShadows = true;
```

### CameraComponent

Entity camera component.

```cpp
struct CameraComponent
```

#### Public members

```cpp
Ref<SceneCamera> Camera;
bool MainCamera = false;
float Fov = 45.0f;
```

*NB: `Camera` is created upon creating this component, it's lifetime is managed so there's no need to worry about it.*

### SkylightComponent

Skylight data, affecting the whole scene.

```cpp
struct SkylightComponent
```

#### Public members

```cpp
EnvironmentMap Map;

bool DynamicSky = true;

float Turbidity = 2.0f;
float Azimuth = 0.0f;
float Inclination = 0.0f;
```

### BoxColliderComponent

Physics box collider.

```cpp
struct BoxColliderComponent
```

#### Public members

```cpp
glm::vec3 HalfExtents = { 0.5f, 0.5f, 0.5f };
glm::vec3 Offset = { 0.0f, 0.0f, 0.0f };

bool IsTrigger = false;
bool AutoAdjustExtent = false;
```

### SphereColliderComponent

Physics sphere collider.

```cpp
struct SphereColliderComponent
```

#### Public members

```cpp
glm::vec3 Offset = { 0.0f, 0.0f, 0.0f };
float Radius = 1.0f;

bool IsTrigger = false;
```

### CapsuleColliderComponent

Physics capsule collider.

```cpp
struct CapsuleColliderComponent
```

#### Public members

```cpp
glm::vec3 Offset = { 0.0f, 0.0f, 0.0f };

float Radius = 1.0f;
float HalfHeight = 1.0f;

bool IsTrigger = false;
```

### CharacterMovementComponent

Physics character movement.

```cpp
struct CharacterMovementComponent
```

#### Public members

```cpp
PhysicsCharacterController* CharacterMovement = nullptr;

float StepOffset = 0.3f;
bool NoGravity = false;
bool ControlMovementInAir = false;
bool ControlRotationInAir = false;
```

*NB: Lifetime of `CharacterMovement` is managed by the PhysicsSystem.*

### RigidbodyComponent

Physics rigidbody.

```cpp
struct RigidbodyComponent
```

#### Public members

```cpp
PhysicsRigidBody* Rigidbody = nullptr;

float Mass = 2.0f;
float LinearDrag = 1.0f;

PhysicsRigidBodyType BodyType = PhysicsRigidBodyType::Dynamic;
uint8_t LockFlags = 0;

MemoryAssetDependency<AssetType::PhysicsMaterial> MaterialAssetID;
```

*NB: Lifetime of `Rigidbody` is managed by the PhysicsSystem.*

### PointLightComponent

Point light data.

```cpp
struct PointLightComponent
```

#### Public members

```cpp
glm::vec3 Radiance = { 1.0f, 1.0f, 1.0f };
float Intensity = 1.0f;
float Multiplier = 1.0f;
float LightSize = 0.5f;
float Radius = 10.0f;
float MinRadius = 1.f;
float Falloff = 1.f;
```

### RelationshipComponent

Entity relationship data, handles child/parent relations.

```cpp
struct RelationshipComponent
```

#### Public members

```cpp
UUID Parent = 0;
std::vector<UUID> ChildrenID;
```

### PrefabComponent

Prefab data, semi-internal component.
This component cannot be added/removed via the editor, and should not be removed via code.

```cpp
struct PrefabComponent
```

#### Public members

```cpp
MemoryAssetDependency<AssetType::Prefab> AssetID;
UUID EntityIDInPrefab = 0;
bool Modified = false;
uint8_t Flags = PrefabUpdateFlag_NoFlags;
```

#### PrefabUpdateFlags

```cpp
enum PrefabUpdateFlags : uint8_t
{
    // Default flags, adds new components, updates the overrides flags and removes 
    // any removed components.
    PrefabUpdateFlag_NoFlags = 0,
    
    // When a component is removed in our local instance, do not respect the change done in the master
    // prefab and keep the component removed.
    PrefabUpdateFlag_DoNotAddRemovedComponents = BIT( 0 ),

    // When a component is added in the master instance, we do not respect that change
    // and keep the component out of our instance.
    PrefabUpdateFlag_DoNotAddAddedComponents   = BIT( 1 ),

    // Do not respect any updates from the master instance.
    PrefabUpdateFlag_IgnoreEverything		   = BIT( 2 ),
};
```

### AudioPlayerComponent

Audio player information.

```cpp
struct AudioPlayerComponent
```

#### Public members

```cpp
MemoryAssetDependency<AssetType::Sound, AssetType::GraphSound> SpecAssetID;
UUID UniqueID;
bool Loop = false;
bool Mute = false;
bool Spatialisation = false;
float Volume = 1.0f;
float Pitch = 1.0f;
Ref<SoundGroup> SoundGroup;
```

### AudioListenerComponent

Audio listener information.

```cpp
struct AudioListenerComponent
```

#### Public members

```cpp
bool Primary = false;
glm::vec3 Direction = TransformComponent::Forward;

// Radians not degrees
float ConeInnerAngle = 0.0f;
float ConeOuterAngle = 0.0f;
```

### BillboardComponent

Billboard data.
This component only has effect in the Editor.

```cpp
struct BillboardComponent
```

#### Public members

```cpp
MemoryAssetDependency<AssetType::Texture> AssetID;
```

### NavigationMeshSpecificationComponent

Navigation data.

Semi-internal component.

This component can only be added via the NavMeshBoundsEntity.
It cannot be removed.

```cpp
struct NavigationMeshSpecificationComponent
```

#### Public members

```cpp
glm::vec3 Extent{};
unsigned int HasBuilt : 1 = 0;
```

### BoneAttachmentInfoComponent

Internal component only added by the Scene system upon calls to AttachToBone, removed when detached.

This component is not duplicatable and can not be added via the SceneHierarchyPanel.

```cpp
struct BoneAttachmentInfoComponent
```

#### Public members

```cpp
std::string AttachmentName;
```

### BehaviourTreeComponent

Data for a behaviour tree.

```cpp
struct BehaviourTreeComponent
```

#### Public members

```cpp
MemoryAssetDependency<AssetType::BehaviourTree> BehaviourTreeAssetID;
```

### TextComponent

Data for worldspace text rendering.

```cpp
struct TextComponent
```

#### Public members

```cpp
std::string Text;
MemoryAssetDependency<AssetType::Font> FontAssetID;
glm::vec4 Color = glm::one<glm::vec4>();
```

