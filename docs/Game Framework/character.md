# Character (SCharacter)

`#include "Saturn/GameFramework/Character.h"`

Player owned and controlled entity with movement supported already setup.

```cpp
class Character : public Entity
```

In some cases this class can also be used by AI Agents if they are being moved by their behaviour tree.

A Character will always add a `CharacterMovementComponent` and a `AudioListenerComponent`, these component should **not** be removed.

!!! info "Please read the following information"

    A Character does not need mesh so therefore it does not add any mesh components, you **must** do that if you want to have a mesh.

For the camera system a character will create and own it's own [CharacterCameraController](charactercameracontroller.md) and by default it will be setup as an FPS camera.

In addtion to this if no camera entity is found the Character will create and own it's own camera entity. The entity will also become it's child regardless of if it owns it or not.

For a third-person camera you should create the camera entity yourself and position where you want and dont forget to call `Setup` in the [CharacterCameraController](charactercameracontroller.md) and specify the camera mode to be `ThirdPerson`.

# Public members

```cpp
Mesh* GetMesh();
const Mesh* GetMesh() const;

//
// Gets the SkeletalMeshComponent (if any)
// 
// So it may return null if this character does not have the component.
//
SkeletalMeshComponent* GetSkeletalMeshComponent();
const SkeletalMeshComponent* GetSkeletalMeshComponent() const;

//
// Gets the StaticMeshComponent (if any)
// 
// So it may return null if this character does not have the component.
//
StaticMeshComponent* GetStaticMeshComponent();
const StaticMeshComponent* GetStaticMeshComponent() const;

// Gets the animation graph (if any)
//
// So it may return null if this character does have an animator.
//
Ref<Animator> GetAnimator();

float GetMovementSpeed();
const float GetMovementSpeed() const;

[[nodiscard]] bool IsSprinting() const;

//
// Change the animation mode from an AnimationController to a single asset.
//
void ChangeAnimationMode( AnimatorType type );

//
// Get Current Animation mode
// 
// @returns the current AnimationMode, you MUST check if the return value
// is not equal to AnimatorType::Unknown, as Unknown means that this character
// doesn't have a SkeletalMeshComponent!
//
[[nodiscard]] AnimatorType GetCurrentAnimationMode() const;

// Phys character controller wrappers

//
// Get the movement component.
// 
// @returns the movement component, it should never be null. TODO: Maybe assert that.
//
CharacterMovementComponent* GetMovementComponent();
const CharacterMovementComponent* GetMovementComponent() const;

//
// Jump
//
// @param pwr - power to jump.
//
void Jump( float pwr = 1.0f );

//
// @returns -- if the character is considered to be "grounded".
//
[[nodiscard]] bool IsGrounded() const;

//
// Move the character controller (and by extension the entity itself) 
// by a certain amount. This value is then added.
//
// @param rDisplacement - displacement vector.
//
void DisplaceCharacterBy( const glm::vec3& rDisplacement );

//
// Stop movement now.
// 
// Set's the linear velocity to zero.
//
void StopMovementImmediately();

// Audio listener

//
// Get the AudioListenerComponent.
// 
// @returns the AudioListenerComponent, it should never be null. TODO: Maybe assert that.
//
AudioListenerComponent* GetAudioListenerComponent();
const AudioListenerComponent* GetAudioListenerComponent() const;

//
// Update the direction this should be after the rotation of the character has changed.
// 
// @param rDirection -- the new direction.
//
void UpdateAudioListenerDirection( const glm::vec3& rDirection );

//
// @returns if the audio listener is the primary one.
//
[[nodiscard]] bool IsPrimaryAudioListener();
```

# Related

[Entity](../Scene/entity.md)
[CharacterCameraController](charactercameracontroller.md)
