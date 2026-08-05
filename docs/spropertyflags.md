# SPropertyFlags

### Flags for an [SProperty](sproperty.md).

32 bit-field enum.

```cpp
enum SPropertyFlags_
```

### Valid flags

```cpp
SPropertyFlags_None = 0,

// NOTE: ReadOnlyInEditor is only available with the editor
SPropertyFlags_ReadOnlyInEditor = BIT( 0 ),

// Help out the build tool, if a Saturn type is in the namespace.
SPropertyFlags_UsingSaturnNamespace = BIT( 1 ), 
```

## Related

[SProperty](sproperty.md)
