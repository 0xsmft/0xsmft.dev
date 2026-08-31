# SClassSpecification

An SClassSpecification defines the specification of an [SClass](sclass.md).

This struct is only to be used by the ClassMetadataHandler and the BuildTool!

```cpp
struct SClassSpecification
```

### Members (public)

```cpp
std::string Name;
std::underlying_type_t<SClassFlags> Flags;
size_t Properties;
size_t Size;
size_t Alignment;
uint64_t Hash;
SClass* pParentClass;
SObject* ( *pClassConstructor )();
SClass* ( *pStaticLinkFunction )();
const SProperty* const* SProperties;
SClassExtendedMetadata ClassExtendedMetadata;
```

## Related

[SClassExtendedMetadata](sclassextendedmetadata.md)
[SClass](sclass.md)
[SClassFlags](sclassflags.md)
[ClassMetadataHandler]()
