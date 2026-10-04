# AssetManager

This class is an owned singleton class responsible for importing assets, deleting assets, asset dependencies, creating assets, asset type traits and purging assets.

```cpp
class AssetManager : public RefTarget
```

As stated above the AssetManager is an owned singleton, meaning that some other class will created the class and will own it. In development configurations this will be in Editor, in distribution this will be the RuntimeLayer.

## Public functions

```cpp
void Tick( Timestep ts );

AssetID CreateAsset( AssetType type );

Ref<Asset> FindAsset( AssetID id );
Ref<Asset> FindAsset( const std::string& rName, AssetType type );

// Note: rPath must be a relative path.
Ref<Asset> FindAsset( const std::filesystem::path& rPath );

template<typename Ty, typename... Args>
Ref<Asset> CreateAssetAs( AssetType type, Args&&... rrArgs );

// Import Asset using Ty
// Where Ty is an asset.
// This will try to find the loaded asset, if it does not exists it will try to load it.
// @return Ref<Ty> if found, nullptr if not
template<typename Ty>
Ref<Ty> GetAssetAs( AssetID id );

// WARNING: THIS WILL PERMANENTLY REMOVE THE ASSET FROM THE REGISTRY REGARDLESS OF ASSET DEPENDENCIES!
void RemoveAsset( AssetID id );

void UpdateAssetDependency( AssetID assetDeleted, AssetID depID, AssetID replacementID );

void UnloadAsset( AssetID id );

AssetID DuplicateAsset( Ref<Asset> asset );

inline const UnorderedAssetMap& GetAssetMap() const;
inline const UnorderedAssetMap& GetLoadedAssetMap() const;

Ref<AssetRegistry>& GetAssetRegistry();
const Ref<AssetRegistry>& GetAssetRegistry() const;

bool IsAssetLoaded( AssetID id );

AssetID PathToID( const std::filesystem::path& rPath );

void Save() const;

template<typename Func>
void Each( Func Function );

[[nodiscard]] bool DoesAssetIDExist( AssetID id ) const;

void BumpAssetVersion();

// NOTE: Automatically saves the Asset Registry
void RenameAsset( AssetID id, const std::string& rName );

// NOTE: Automatically saves the Asset Registry
void UpdateAssetPathsOnRename( const std::filesystem::path& rOldPath, const std::filesystem::path& rNewPath );

size_t GetAssetRegistrySize() const;

// Memory Asset Dependencies
void RegisterMemoryAssetDependency( AssetID dependencyID, MemoryAssetDependencyBase* pBase );
void UnregisterMemoryAssetDependency( AssetID dependencyID, MemoryAssetDependencyBase* pBase );

const std::unordered_map<AssetID, std::unordered_set<MemoryAssetDependencyBase*>> GetAssetDependencies() const;

const std::unordered_set<MemoryAssetDependencyBase*> GetAssetDependenciesForAsset( const Ref<Asset> asset ) const;
[[nodiscard]] bool DoesAssetHaveDependencies( Ref<Asset> asset );

// Asset Dependencies, i.e. asset interdependence, known as "Pure Dependencies" in the Engine.

// 
// Register an Asset Dependency
//
// @param assetID the asset that will depend on dependencyID (the dependee)
// @param dependencyID the dependency ID
// 
void RegisterAssetDependency( AssetID assetID, AssetID dependencyID );

// 
// Unregister an Asset Dependency
//
// @param assetID the asset that will no longer depend on dependencyID (the dependee)
// @param dependencyID the dependency ID
// 
void UnregisterAssetDependency( AssetID assetID, AssetID dependencyID );

// 
// Unregister all Asset Dependencies
//
// @param assetID the asset that will it's dependencies cleared (the dependee)
// 
void UnregisterAllAssetDependencies( AssetID assetID );

// 
// Check is an Asset has any dependencies
//
bool CheckPureAssetDependencies( Ref<Asset> asset );

// Works on Pure dependencies (asset interdependence) only!
// Checks if the asset that this dependency needs/is, still exists in the Registry.
void SanitiseAssetDependencies();

const std::unordered_map<AssetID, std::unordered_set<AssetID>> GetPureAssetDependencies() const;
const std::unordered_set<AssetID> GetPureAssetDependenciesForAsset( const Ref<Asset> asset ) const;

AssetTypeTraits& GetAssetTypeTrait( AssetType type );
const AssetTypeTraits& GetAssetTypeTrait( AssetType type ) const;

[[nodiscard]] bool IsAssetTypeReimportable( AssetType type ) const;
```

## Releated

[Asset](asset.md)
[AssetRegistry](assetregistry.md)
[AssetTypeTraits](assettypetraits.md)
