# UUID

`#include "Saturn/Core/UUID.h"`

64-bit unsigned universally unique identifier.

```cpp
class UUID
```
Mainly used for IDs, such as AssetIDs, Entity UUIDs etc.

This type is hashable in standard library map types.

This type is also printable in `std::format()`.

By convention a UUID with a value of 0 is considered to be invalid.

## Public members

```cpp
// Generate new ID
UUID();
UUID( uint64_t uuid );
UUID( const UUID& other );

operator uint64_t();
operator const uint64_t() const;
```

## Private Members

```cpp
uint64_t m_UUID = 0llu;
```
