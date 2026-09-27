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
```

## Related
