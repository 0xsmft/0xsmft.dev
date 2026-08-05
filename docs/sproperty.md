# SProperty

An SProperty wraps a reflected C++ type.

Any value that is preceeded with the `SPROPERTY()` macro
will be picked up by the HeaderTool and the value will
become reflected.

A value that's like:

```cpp
SPROPERTY()
float m_spHealth = 0.0f;
```

Will become relfected and will be viewable in the Editor.

SProperty's are set via the SObject's internal class.

```cpp
class SProperty
```
### Functions (public)

```cpp
// Set a the value.
template<typename CppType>
void SetProperty( SObject* pObject, CppType value );

inline void SetFlag( SPropertyFlags flag, bool value );

[[nodiscard]] bool IsFlagSet( SPropertyFlags flag ) const;
SPropertyFlags GetFlags() const;

const std::string& GetName() const;
const std::string& GetNativeType() const;

SPropertyType GetType() const;

inline void SetType( SPropertyType type );
inline void SetNativeType( const std::string& rNativeType );
inline void SetName( const std::string& rName );

void Serialise( const SObject* pObject, std::ofstream& rStream ) const;
void Deserialise( SObject* pObject, std::istream& rStream );

// Get the property, returning the best return type described in the PropertyTypeTraits.
template<SPropertyType Ty>
[[nodiscard]] typename PropertyTypeTraits<Ty>::Type Read( SObject* pObject ) const;

template<SPropertyType Ty>
[[nodiscard]] typename PropertyTypeTraits<Ty>::Type Read( SObject* pObject );

// Return a _copy_ of the value.
template<typename Ty>
[[nodiscard]] const Ty GetCopy( const SObject* pObject ) const;

template<typename Ty>
[[nodiscard]] Ty GetCopy( const SObject* pObject );

// Copy the modified SProperty value from pSrcObject to pDstObject.
void RtCopyFromOther( const SObject* pSrcObject, SObject* pDstObject ) const;
```

### Members (protected)

```cpp
std::string m_Name;
// HEADER TOOL ONLY!, stores the native C++ type, i.e. float, bool, int, double but as a string.
std::string m_NativeType;

SPropertyType m_Type = SPropertyType::Unknown;
SPropertyFlags m_Flags = SPropertyFlags_None;
```

### Members (private)

```cpp
// Function ptr to get function in the internal SClass.
const void* m_pGetPropertyFunction = nullptr;
// Function ptr to set function in the internal SClass.
const void* m_pSetPropertyFunction = nullptr;
```
## Related

[SClass](sclass.md) [SObject](sobject.md) [SPropertyFlags](spropertyflags.md) [SPropertyType](spropertytype.md) [PropertyTypeTraits](propertytypetraits.md)
