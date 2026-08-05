# PropertyTypeTraits

Compile time templated structure to get information about an SProperty data type.

```cpp
template<SPropertyType Type>
struct PropertyTypeTraits;
```

## Declared as

```cpp
#define SAT_CREATE_PROPERTY_TYPE_TRAIT(PropertyType, CppType, IsRef, PrefConstRef) \
template<> struct PropertyTypeTraits<SPropertyType::PropertyType> \
	{  \
		using Value = CppType;  \
		using Reference = CppType&; \
		using Const = const CppType; \
		using ConstReference = const CppType&; \
		\
		using NeedsToBeReference = std::bool_constant<IsRef>; \
		using PreferConstReference = std::bool_constant<PrefConstRef>; \
		using Type = std::conditional_t<NeedsToBeReference::value, std::conditional_t<PreferConstReference::value, ConstReference, Reference>, std::conditional_t<PreferConstReference::value, ConstReference, Value>>; \
	}
```

## Members (public)

```cpp
using Value = CppType;
using Reference = CppType&;
using Const = const CppType;
using ConstReference = const CppType&;

using NeedsToBeReference = std::bool_constant<IsRef>;
using PreferConstReference = std::bool_constant<PrefConstRef>;

using Type = std::conditional_t<NeedsToBeReference::value, std::conditional_t<PreferConstReference::value, ConstReference, Reference>, std::conditional_t<PreferConstReference::value, ConstReference, Value>>;
```

The return type of the property is defined in the `Type` alias, the table below can help:

| NeedsToBeReference | PreferConstReference  | Type 
| ------| ------|----- | 
| ✅ | ✅ | `ConstReference` |
| ✅ | ❌ | `Reference` |
| ❌ | ❌ | `Value` |

## Default type traits

| SType | C++ Type  | IsRef | PrefConstRef | 
| ------| ------|----- | ---- |
| `Double` | `double` | ❌ | ❌
| `Float` | `float` | ❌ | ❌
| `Uint8` | `uint8_t` | ❌ | ❌
| `Uint15` | `uint16_t` | ❌ | ❌
| `Uint32` | `uint32_t` | ❌ | ❌
| `Uint64` | `uint64_t` | ❌ | ❌
| `Int8` | `int8_t` | ❌ | ❌
| `Int16` | `int16_t` | ❌ | ❌
| `Int32` | `int32_t` | ❌ | ❌
| `Int64` | `int64_t` | ❌ | ❌
| `Vector2` | `glm::vec2` | ✅ | ✅
| `Vector3` | `glm::vec3` | ✅ | ✅
| `Vector4` | `glm::vec4` | ✅ | ✅
| `String` | `std::string` | ✅ | ✅
| `Asset` | `AssetID` | ❌ | ❌
| `EntityType` | `SharedPtr<Entity>` | ❌ | ❌
| `Class` | `SClass*` | ❌ | ❌
| `Unknown` | `void*` | ❌ | ❌


## Related

[SPropertyType](spropertytype.md)
