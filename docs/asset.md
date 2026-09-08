# Asset

Saturn Asset class & base class for all assets.

```cpp
class Asset : public RefTarget
```

## Public memebers

```cpp
// The relative path to this Asset.
// Relative to the project root path, e.g. Assets/Textures/Floor.png
std::filesystem::path Path;
std::string Name;

AssetID ID = 0;
AssetType Type = AssetType::Unknown;
AssetVersion Version = AssetVersion::Latest;
```
## Public Functions

```cpp
// Path must be an absolute path.
// If you want to set a relative path just modify the 'Path' variable directly and update the name accordingly.
// NB: This will update the Name as well!
void SetAbsolutePath( const std::filesystem::path& rPath );

#if !defined(SAT_DIST)
// Called when this asset is about to be deleted,
// use this if this asset needs to clean up before its deleted,
// for example, any type of mesh needs to also delete its source file or for sounds they need to do the same.
virtual void OnDelete() {}

// Called when an Asset Dependency needs to be replaced with a new ID.
virtual void OnAssetDependencyReplace( AssetID oldID, AssetID newID ) {}
#endif

//
// Returns true if this asset can be purged
// and can be unloaded.
// 
// NB: Do not check the ref-count if this asset
// the AssetManager already does that before
// this is even called, so if this is called
// the ref-count is 1 and the AssetManager
// needs confirmation.
//
virtual bool CanPurge() const { return true; }

//////////////////////////////////////////////////////////////////////////
// #WARNING This should not be confused with AssetSerialisers. This is for raw binary serialisation! (see: AssetBundle)

void SerialiseData( std::ofstream& rStream ) const;
void DeserialiseData( std::ifstream& rStream );
```

## Related

[AssetType](assettypes.md)
[AssetTypeTraits](assettypetraits.md)
[AssetVersion](assetversion.md)
