# PhysicsRigidBody

`#include "Saturn/Physics/PhysicsRigidBody.h"`

Represents a static/dynamic/kinematic rigid body.

```cpp 
class PhysicsRigidBody : public RefTarget
```

A rigidbody is created and managed by the PhysicsFoundation, but a rigidbody needs an Entity in order to be created.

A rigidbody can be static, kinematic or dynamic.
See [PhysicsBodyType](physicsbodytype.md) for more information.

The position and rotation of the *entity* may be controlled by the rigidbody, this will depend on the locking flags and what rigidbody type it is.

For dynamic rigidbodies:

- Position and rotation is controlled by the rigidbody, some rotational axes may not but depends on locking flags.

For static rigidbodies:

- Position and rotation is controlled by the rigidbody and can not be moved.

For kinematic rigidbodies:

- Position and rotation is controlled via the entity, moving kinematic bodies can be expensive to do so and you must also manaully call `PhysicsRigidBody::SetPosition` after.

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

[PhysicsBodyType](physicsbodytype.md)
[RigidbodyLockFlags](rigidbodylockflags.md)
