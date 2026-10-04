# PhysicsRigidBody

`#include "Saturn/Physics/PhysicsRigidBody.h"`

Represents a static/dynamic/kinematic rigid body.

```cpp 
class PhysicsRigidBody : public RefTarget
```

A rigidbody is created and managed by the PhysicsFoundation, but a rigidbody needs an Entity in order to be created.

A rigidbody can be static, kinematic or dynamic.
See [PhysicsBodyType](physicsbodytype.md) for more information.

## Public members

```cpp
void SetMass( float val );
void SetLinearDrag( float value );
void SetLinearVelocity( const glm::vec3& rVelocity );
float GetLinearDrag();
void ApplyForce( glm::vec3 ForceAmount, ForceMode Type );
void Rotate( const glm::vec3& rRotation );
void Rotate( const glm::quat& rRotation );
void SetPosition( const glm::vec3& rPosition );

void SyncTransfrom();

glm::vec3 GetPosition() const;
glm::vec3 GetRotation() const;

glm::vec3 GetLinearVelocity() const;

void SetLockFlags( RigidbodyLockFlags flags, bool value );
bool IsFlagSet( RigidbodyLockFlags flags ) const;
RigidbodyLockFlags GetFlags() const;

bool AllRotationLocked() const;

SharedPtr<Entity> GetEntity();
Ref<PhysicsShape> GetShape();
JPH::BodyID GetBodyID() const;
```

## Related

[PhysicsBodyType](phyiscsbodytype.md)
[PhysicsBodyType](phyiscsbodytype.md)