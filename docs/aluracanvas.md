# Alura Canvas

Main UI functions for Alura.

Global variable: `AluraCanvas* g_AluraCanvas`

The origin of the viewport is top-left as described in [Maths](maths.md)

Only one `AluraCanvas` can exist, any attempt to create a second `AluraCanvas` will cause the application to assert.

```cpp
class AluraCanvas : public RefTarget
```

### UI Functions (public)

```cpp
void AddRect( const glm::vec2& rSize, float rounding = 0.0f, const glm::vec4& rColour = glm::one<glm::vec4>() );
void AddImage( const glm::vec2& rSize, Ref<Texture2D> image, const glm::vec4& rColour = glm::one<glm::vec4>(), const glm::vec2& rUV1 = { 0.0F, 1.0F }, const glm::vec2& rUV2 = { 1.0F, 0.0F } );

[[nodiscard]] bool AddImageButton( const glm::vec2& rSize, Ref<Texture2D> image, const glm::vec4& rColour = glm::one<glm::vec4>(), const glm::vec2& rUV1 = { 0.0F, 1.0F }, const glm::vec2& rUV2 = { 1.0F, 0.0F } );

// NOTE: fraction is a normalised value between 0.0 - 1.0, because we are working with the percent in decimal from.
void AddProgressBar( float fraction, const glm::vec2& rSize );

void AddText( const std::string& rText );
void AddTextColoured( const std::string& rText, const glm::vec4& rColour );

template<typename... Args>
void TextFormatted( std::format_string<Args...> fmt, Args&&... rrArgs );

void AddTextU32( const std::u32string& rText );
void AddTextColouredU32( const std::u32string& rText, const glm::vec4& rColour );

[[nodiscard]] bool AddButton( const glm::vec2& rSize, const glm::vec4& rColour = glm::one<glm::vec4>() );

// Add a button with text.
// If no size is specified then Alura will calculate the spacing needed.
[[nodiscard]] bool AddButton( const std::string& rText, const glm::vec2& rSize = glm::zero<glm::vec2>() );

void AddCircle( float radius, float thinkness = 1.0f, bool filled = false, const glm::vec4& rColour = glm::one<glm::vec4>() );

[[nodiscard]] bool AddCheckbox( const std::string& rLabel, bool* pValue );
[[nodiscard]] bool AddCheckboxRight( const std::string& rLabel, bool* pValue );

[[nodiscard]] bool AddInputText( const std::string& rLabel, std::string* pStr, AluraTextInputFlags flags = AluraTextInputFlags_NoFlags );

//
// Begin a combo box
// 
// A combo box is a small popup that automatically calculates it's size upon the first frame
// 
// NB: You must check the return value of this function, if it succeeds you call 
// EndComboBox() after.
//
[[nodiscard]] bool BeginComboBox( const std::string& rLabel, const std::string& rPreviewName, float maxSize = 0.0f );

// End the current combo box.
void EndComboBox();

//
// Draw a slider value
// 
// @param rLabel - the label to appear on the left hand side of the slider
// @param rPercent - the value
// @param maxSliderSize - the maximum extent of the slider on the X axis, by default this value
// is zero meaning that a region must be used to calculate the content size, if you aren't using a 
// region the you _must_ specify a size!
// 
// @returns - if the slider value was modified.
//
[[nodiscard]] bool AddSliderFloat( const std::string& rLabel, float& rValue, float minValue = 0.0f, float maxValue = 100.0f, float maxSliderSize = 0.0f );

[[nodiscard]] bool AddPopup( const std::string& rLabel );
void CloseCurrentPopup();
inline void MarkPopupAsClosed() { CloseCurrentPopup(); }
void EndPopup();

[[nodiscard]] bool IsPopupOpenAndVisible( const std::string& rName ) const;
[[nodiscard]] bool IsPopupOpen( const std::string& rName ) const;
[[nodiscard]] bool IsPopupVisible( const std::string& rName ) const;

void OpenPopup( const std::string& rName );

//
// Horizontal line from start to end taking up the whole region size on the X axis.
//
// NB: An active region must exist.
//
void AddSeparator();

//
// Begin a region.
// 
// A region is an area where all widgets can be drawn on.
//
// You must check the return value if it succeeds you call 
// EndRegion() after.
//
[[nodiscard]] bool BeginRegion( const std::string& rID, const glm::vec2& rBounds );
void EndRegion();

//
// Key button. A button that has a key code and text to the right of it.
// 
// e.g. [F] To pay respects.
//
[[nodiscard]] bool AddKeyButton( const std::string& rLabel, RubyKey key );

void AddDummy( const glm::vec2& rSize );

void DrawDemo();
```

### Auxiliary (public)

```cpp
void SetNextItemPosition( const glm::vec2& rPosition );

void Indent( float width = 0.0f );
void Unindent( float width = 0.0f );

void AlignNextItemCenterXY( const glm::vec2& rSize );
void AlignNextItemCenterX( const glm::vec2& rSize );

// Add rOffset to the next item position.
void NudgeNextItemPosition( const glm::vec2& rOffset, bool addItemSpacing = true );

void SameLine( float offset = 0.0f, float spacing = -1.0f );

void PushStyle( std::underlying_type_t<AluraColour> index, const glm::vec4& rNewValue );
void PopStyle();

void PushFontSize( float newSize );
void PopFontSize();

float GetFrameHeight() const;
float GetRegionMaxScroll( const AluraRegionData& rData ) const;

// An active region must be pushed before calling this.
glm::vec2 GetContentRegionAvail();

[[nodiscard]] glm::vec2 CalcTextSize( const std::string& rText );
[[nodiscard]] glm::vec2 CalcTextSizeN( const std::string& rText, size_t n );
[[nodiscard]] glm::vec2 CalcTextSizeNAtOffset( const std::string& rText, size_t n, size_t off );

[[nodiscard]] bool IsAnyItemHot() const;
[[nodiscard]] bool IsAnyRegionHot() const;
[[nodiscard]] bool IsAnyItemActive() const;
[[nodiscard]] bool IsAnyItemFocused() const;
[[nodiscard]] bool IsAnyItemSelected() const;

glm::vec2 GetPosition() const;
glm::vec2 GetSize() const;

float GetWidth() const;
float GetHeight() const;

glm::vec2 GetCursorPosition() const;

const AluraStyle& GetStyle() const;
AluraStyle& GetStyle();

Ref<AluraFont> GetActiveFont() const;
Ref<AluraFont> GetEditorFont() const;
```

## Related

[AluraCanvasSpecification](aluracanvasspecification.md)
[AluraFont](alurafont.md)
[AluraColour](aluracolour.md)
[AluraStyle](alurastyle.md)
