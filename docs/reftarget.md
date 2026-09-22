# RefTarget

``#include "Saturn/Core/Ref.h"``

Base class for all intrusive reference counted objects.

```cpp
class RefTarget
```
## Public members

```cpp
virtual ~RefTarget() = default;

inline void AddRef() const;
inline void RemoveRef() const;
inline uint32_t GetRefCount() const;
```

## Private members

```cpp
mutable std::atomic_uint m_RefCount{ 0u };
```