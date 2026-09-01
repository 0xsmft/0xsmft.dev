# AluraStyle

Style properties for Alura.

```cpp
class AluraStyle
```

### Members (public)

```cpp
// Default alpha for items.
float Alpha;

// Default disabled alpha for items.
float DisabledAlpha;

// Region Rounding, 0.0f by default.
float RegionRounding;

// Spacing between the first element and the canvas.
glm::vec2 WindowPadding;

// Spacing between each item.
glm::vec2 ItemSpacing;

// The spacing between items and their inner elements
// e.g. button and the text inside of the button.
glm::vec2 ItemInnerSpacing;

// Indent offset
float IndentSpacing;

// Border size of the canvas.
float WindowBorderSize;

// Current font size.
float CurrentFontSize;

// Colors
std::array<glm::vec4, ( std::underlying_type_t<AluraColour> )AluraColour_Count> Colours;
```

### Functions (public)

```cpp
void Default();
```

## Related

[AluraColour](aluracolour.md)
[AluraStyleVar](alurastylevar.md)
