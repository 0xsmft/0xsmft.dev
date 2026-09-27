# RubyWindow

``#include "Saturn/Core/Ruby/RubyWindow.h"``

This class is responsible for creating and managing a single window.

To create a window you must first create a [RubyWindowSpecification](rubywindowspecification.md) and pass that specification into the window.

RubyWindow acts a wrapper to the lower level RubyWindowBackend class.

The current RubyWindowBackend class depends on the current operating system.

```cpp
class RubyWindow : public RefTarget
```
This class is non-copyable.

## Public members

```cpp
void Maximize();
void Minimize();
void Restore();
void Resize( uint32_t Width, uint32_t Height );
void Show( RubyWindowShowCmd Command = RubyWindowShowCmd::Default );
void Hide();
void SetPosition( int x, int y );
void SetMousePos( double x, double y );
RubyVec2 GetMousePos();
void SetMouseCursor( RubyCursorType Cursor );
void SetMouseCursorMode( RubyCursorMode mode );
void ChangeTitle( const std::string& rTitle );
void ChangeTitle( const std::wstring& rTitle );
void SetClipboardText( const std::string& rTextData );
void SetClipboardText( const std::wstring& rTextData );
void Focus();
void FlashAttention();
void CentreWindowXYInMonitor();
void Close();

// Set a 32x32 (preferred) RGBA texture that is not flipped vertically.
void SetIcon( Ref<class Texture2D> icon );

RubyIVec2 GetPosition();
RubyIVec2 GetLastMousePos()  const;
RubyIVec2 GetVirtualMousePos() const;
RubyCursorMode GetCursorMode()  const;
RubyCursorMode GetLastCursorMode() const;
RubyIVec2 GetSize()   const;

//
// Window size in pixels
//
// This may be the same as the size returned in GetSize()
// however on Retina displays this will be the window size
// multiplied by the framebuffer scale factor.
//
RubyIVec2 GetFramebufferSize() const;

RubyVec2 GetFramebufferScale() const;   		

RubyGraphicsAPI GetGraphicsAPI() const;
RubyStyle GetStyle() const;

std::string  GetClipboardText();
std::wstring GetClipboardTextW();

uint32_t  GetWidth()  const;
uint32_t  GetHeight() const;
uint32_t  GetFramebufferWidth()  const;
uint32_t  GetFramebufferHeight() const;

[[nodiscard]] bool IsFocused();
[[nodiscard]] bool Minimized();
[[nodiscard]] bool Maximized();
[[nodiscard]] bool ShouldClose();
[[nodiscard]] bool IsKeyDown( RubyKey key );
[[nodiscard]] bool IsMouseButtonDown( RubyMouseButton button );
[[nodiscard]] bool MouseInWindow();

double GetTime() const;

template<typename Ty, typename... Args>
bool DispatchEvent( EventType Type, Args&&... args )
{
    Ty event( Type, std::forward<Args>( args )... );

    if( m_pEventTarget )
        return m_pEventTarget->OnEvent( event );

    return false;
}
```

## Protected members

```cpp
// Only used for borderless windows.
uint32_t m_TitlebarHeight = 0;
bool m_TitlebarCondition = false;

RubyCursorMode m_CursorMode = RubyCursorMode::Normal;
RubyCursorMode m_LastCursorMode = RubyCursorMode::Normal;

RubyWindowShowCmd m_ShowCommand = RubyWindowShowCmd::Fullscreen;

RubyIVec2 m_LockedMousePosition{};
RubyIVec2 m_LastMousePosition{};

RubyPerfTimer m_Timer;
```

## Private members

```cpp
std::unique_ptr<RubyBackendBase> m_pDefaultBackend = nullptr;
```
