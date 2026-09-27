# SClassFlags

``#include "Saturn/GameFramework/SClass.h"``

Flags for an [SClass](sclass.md).

32 bit-field enum.

```cpp
enum SClassFlags
```

### Valid flags

```cpp
SC_None

// DO NOT SET! This flag is set by the reflection system itself!
SC_Initialised = 1 << 0,

// Is the class abstract
SC_Abstract   = 1 << 1,

// If a class is spawnable it means that it can be spawned into the scene.
SC_Spawnable  = 1 << 2,

// Visible in editor means that this class will appear when selecting a new class on the "Create a class" modal.
SC_VisibleInEditor = 1 << 3,

// By default classes have extended metadata, which means that classes will have their header path as path of the
// SClass, it's currently only used for game classes.
SC_NoExtendedMetadata = 1 << 4,

// Deprecated
SC_External = 1 << 5,
```

## Related

[SClass](sclass.md)
[ClassMetadataHandler](classmetadatahandler.md)
