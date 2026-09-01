# Entity (SEntity)

Base class for a spawnable gameplay object.

```cpp
SCLASS()
class Entity : public SObject
```

### Most Important Functions (public)

```cpp
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
