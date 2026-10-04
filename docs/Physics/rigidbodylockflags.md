# RigidbodyLockFlags

`#include "Saturn/Physics/PhysicsShapeTypes.h"`

Bit field enum for locking axes of movement and rotation for a [PhysicsRigidBody](physicsrigidbody.md).

```cpp
enum RigidbodyLockFlags : uint8_t
```

## Flags

```cpp
RigidbodyLock_PositionX = BIT( 0 ),
RigidbodyLock_PositionY = BIT( 1 ),
RigidbodyLock_PositionZ = BIT( 2 ),
RigidbodyLock_RotationX = BIT( 3 ),
RigidbodyLock_RotationY = BIT( 4 ),
RigidbodyLock_RotationZ = BIT( 5 ),

RigidbodyLock_AllPosition = RigidbodyLock_PositionX | RigidbodyLock_PositionY | RigidbodyLock_PositionZ,
RigidbodyLock_AllRotation = RigidbodyLock_RotationX | RigidbodyLock_RotationY | RigidbodyLock_RotationZ,

RigidbodyLock_AllAxes = RigidbodyLock_AllPosition | RigidbodyLock_AllRotation,

```
