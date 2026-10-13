# CharacterCameraController

`#include "Saturn/GameFramework/CharacterCameraController.h"`

This class responsible for managing and controlling the camera movement within a [Character](character.md).

The controller supports two different camera modes, first-person and third-person.

By default the camera will be setup as a first person camera.

The camera controller is allocated on the stack and is owned by the Character.

```cpp
class CharacterCameraController
```

## Public members

```cpp
void Update();

void Setup( Ref<class Camera> camera, SharedPtr<class Entity> camEntity, CharacterCameraControllerMode desiredMode );

//
// Get right vector
//
glm::vec3 GetRight() const;

//
// Get forward vector
//
glm::vec3 GetForward() const;

float GetMouseUpMovement() const;
float GetMouseSensitivity() const;
```
## Related

[Character](character.md)
[CharacterCameraControllerMode](charactercameracontrollermode.md)
