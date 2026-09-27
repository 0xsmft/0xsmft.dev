# SClass

``#include "Saturn/GameFramework/SClass.h"``

An SClass defines the type of an [SObject](sobject.md).

```cpp
SCLASS()
class SClass : public SObject
```

### Functions (public)

```cpp
// Construct the SObject that this SClass defines.
SObject* CreateDefaultObject();
SObject* CreateDefaultObject() const;

SClassFlags GetFlags() const;
const std::string& GetName() const;

size_t GetSize() const;
size_t GetAlignment() const;
uint64_t GetHash() const;

void SetFlag( SClassFlags flag );

const SClass* GetParentClass() const;
int GetPropertyCount() const;
const SProperty* const* GetProperties() const;

SProperty& GetProperty( const std::string& rPropertyName ) const;
bool IsChildOf( const SClass* pBase ) const;
```

### Static API

```cpp
// Construct an SClass via it's SClassSpecification
static void RConstructClass();
static void RConstructClassHotReloaded();
static void ProcessNewlyLoadedSClasses();
```

## Related

[SClassSpecification](sclassspecification.md)
[SObject](sobject.md)
[SProperty](sproperty.md)
[ClassMetadataHandler]()
