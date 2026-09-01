# AluraCanvasSpecification

Specification to create an [AluraCanvas](aluracanvas.md).

```cpp
struct AluraCanvasSpecification
```
### Members (public)

```cpp
// Pixel size of the canvas.
glm::vec2 Size{};

// Position of the canvas relative to the window top-left.
glm::vec2 Position{};

// Specify the main font for this canvas to use.
AssetID MasterFontAssetID = 0llu;

// Specify the main styling profile to be used, you don't need to have a styling profile asset
// as Alura will automatically default the style if no profile is specified.
AssetID StylingProfile = 0llu;
```

## Related

[AluraCanvas](aluracanvas.md)
[AluraFont](aluracanvas.md)
[AluraStylingProfile](aluracanvas.md)
