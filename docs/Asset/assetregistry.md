# AssetRegistry

`#include "Saturn/Asset/AssetRegistry.h"`

The `AssetRegistry` is the class that resposible for a holding a list of all assets and all currently loaded assets.

```cpp
class AssetRegistry : public RefTarget
```

It essentially wraps a `*.sreg` file.

The [AssetManager](assetmanager.md) holds a reference to an AssetRegistry.

## Public members

```cpp
AssetID CreateAsset( AssetType type );
Ref<Asset> FindAsset( AssetID id );

Ref<Asset> FindAsset( const std::filesystem::path& rPath );
Ref<Asset> FindAsset( const std::string& rName, AssetType type );

std::vector<AssetID> FindAssetsWithType( AssetType type ) const;

AssetID PathToID( const std::filesystem::path& rPath );

void RemoveAsset( AssetID id );
void DestroyAsset( AssetID id );

[[nodiscard]] bool DoesIDExists( AssetID id ) const;

size_t GetSize() const;

const UnorderedAssetMap& GetAssetMap() const;
const UnorderedAssetMap& GetLoadedAssetsMap() const;

std::filesystem::path& GetPath();
const std::filesystem::path& GetPath() const;
```

## Related

[AssetManager](assetmanager.md)