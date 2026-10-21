# Input

`#include "Saturn/Core/Input.h"`

Always lazily-loaded singleton for input states.

```cpp
class Input
```

The main purpose of this class is to ensure when the mouse cursor mode can be set, however this responsibility only exists on development build configurations.

## Public members

```cpp
bool KeyPressed( RubyKey key );
bool MouseButtonPressed( RubyMouseButton button );

float MouseX();
float MouseY();

glm::vec2 MousePosition();
glm::vec2 MousePositionRelativeToAppWindow();

void SetCursorMode( RubyCursorMode mode, bool bypassGuard = false );
RubyCursorMode GetCursorMode();

/// vvvv the following are only for development
#if !defined(SAT_DIST)
    void SetCanSetCursorMode( bool val );
    bool CanSetCursorMode() const;
#endif
// ^^^^ only on development
```

## Related

[RubyCursorMode](Ruby/rubycursormode.md)
[RubyKey](Ruby/rubykey.md)
[RubyMouseButton](Ruby/rubymousebutton.md)
