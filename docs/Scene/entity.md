# Entity (SEntity)

``#include "Saturn/Scene/Entity.h"``

Base class for a spawnable gameplay object.

```cpp
SCLASS()
class Entity : public SObject
```

### Most Important Functions (public)

```cpp
// Called when the Runtime begins or when this entity is spawned
virtual void BeginPlay();

// Called every frame with a potentially variable timestep 
virtual void OnUpdate( Saturn::Timestep ts );

// Called every frame with a fixed timestep 
virtual void OnPhysicsUpdate( Saturn::Timestep ts );

// When this entity hits another entity with a physics body, or a trigger.
virtual void OnEntityHit( Entity* pOther, bool isTrigger );

// When this entity is no longer in the trigger or the entity.
virtual void OnEntityLeave( Entity* pOther, bool isTrigger );

template<typename T, typename... Args>
T& AddComponent( Args&&... args );

// NB: Will assert if T is not found in the entity! Use TryGetComponent instead!
template<typename T>
[[nodiscard]] T& GetComponent();

// NB: Will assert if T is not found in the entity! Use TryGetComponent instead!
template<typename T>
[[nodiscard]] const T& GetComponent() const;

template<typename T>
[[nodiscard]] bool HasComponent() const;

template<typename... T>
[[nodiscard]] bool HasComponents() const;

template<typename T>
void RemoveComponent();

template<typename... T>
void RemoveComponents();

template<typename T>
[[nodiscard]] T* TryGetComponent();

template<typename T>
[[nodiscard]] const T* TryGetComponent() const;

glm::vec3 GetLocalPosition() const;
glm::vec3 GetLocalRotation() const;
glm::quat GetLocalRotationQuat() const;
glm::vec3 GetLocalScale() const;

//
// @returns the physics material ID.
// 
// Priority is given to the RigidBody then the Static/Skeletal Meshes.
// May return zero if no ID is set or could be found.
//
UUID GetPhysicsMaterialID();

//
// Helper to remove this entity from it's parent.
//
void RemoveFromParent();

//
// Move to a new parent and remove from the old parents list.
//
void ChangeToNewParent( SharedPtr<Entity> parent );

//
// Try to get the parent.
// 
// @returns -- the parent (if any, may be null if not found.)
//
[[nodiscard]] SharedPtr<Entity> TryGetParent();
[[nodiscard]] const SharedPtr<Entity> TryGetParent() const;

//
// Attach this entity to a bone in it's parent.
//
void AttachToBone( const std::string& rAttachmentName );

//
// Attach this entity to a bone in a new parent.
//
void AttachToBone( SharedPtr<Entity> parent, const std::string& rAttachmentName );

//
// Remove this entity from a bone attachment.
//
void DetachFromBone();

//
// Calculate forward vector based from the
// entity's _local_ rotation.
//
glm::vec3 CalculateForwardVectorFromRotation();
```

## Related
