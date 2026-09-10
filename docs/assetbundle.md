# AssetBundle

The AssetBundle is a compressed collection of all assets in the current project.

The threshold at which an asset would be compressed is specified in the project settings. By default it's 512kib.

```cpp
class AssetBundle
```

## Structure

The AssetBundle needs at least two files to work, `AssetBundle.sab` and `AssetBundle-Minimal.sab`

### AssetBundle-Minimal (AB-Minimal)

The easiest to explain is the Minimal asset bundle it contains the needed information for about the project that we are trying to load.

The bundle includes:

- Project Name
- Startup Scene ID
- Developer Version (since 0.2.7)
- Default Material ID
- Default Physics Material ID
- Default Font Asset
- All action bindings
- All Sound Groups

#### File structure

The file structure of AB-Minimal includes a 4-byte file signature `0x2E, 0x41, 0x42, 0x00` (`.AB` + null-byte), followed by a 4-byte unsigned int for the [Engine Version](versions.md) and then an 8-byte unsigned int for the Unix Timestamp upon which this bundle was built.

The file then follows the same stucture as listed in the previous section.

| Byte | Value |
| ------ | ---- |
0-3 | Signature
4-7 | Version
7-15 | Unix Timestamp
16-n | Remaning project data

## Public Members (static)

```cpp
[[nodiscard]] static AssetBundleResult BundleAssets( Ref<JobProgress> jobProgress );
[[nodiscard]] static AssetBundleResult ReadBundle();

              static AssetBundleResult BundleMinimal();
[[nodiscard]] static AssetBundleResult ReadMinimal();
```

