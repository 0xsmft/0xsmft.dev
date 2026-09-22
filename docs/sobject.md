# SObject

``#include "Saturn/GameFramework/SObject.h"``

Base class for Gameplay Objects/Reflected types.

All classed based from `SObject` should have the `S` prefix.

```cpp
class SObject : public RefTarget
```

### Functions (public)

```cpp
const SClass* GetClass() const;
SObject* GetParentObject() const;
```

### Private members

```cpp
// The class that we are an instance of.
SClass* m_pClass;

// The object that we reside in.
SObject* m_pParentObject;
```

## Related

[SClass](sclass.md)
