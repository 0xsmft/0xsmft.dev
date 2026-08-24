# SPropertyType

### Valid data types for an [SProperty](sproperty.md).

```cpp
enum class SPropertyType
```

### Valid flags

```cpp
Double,
Float,
Uint8,
Uint16,
Uint32,
Uint64,
Int8,
Int16,
Int32,
Int64,
Vector2, /* glm::vec3 */
Vector3, /* glm::vec2 */
Vector4, /* glm::vec4 */
String, /* std::string */
Asset, // AssetID
EntityType, // SharedPtr<Entity>
Class,
Unknown
```

## Related

[SProperty](sproperty.md)
