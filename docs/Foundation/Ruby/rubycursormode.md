# RubyCursorMode

`#include "Saturn/Core/Ruby/RubyCore.h"`

Enum for cursor mode.

```cpp
enum class RubyCursorMode : uint8_t
```

## Values

```cpp
Normal,

// Mouse is hidden but still uses real OS mouse positions
Hidden,

// Mouse is hidden however mouse is clipped in Window bounds and Ruby provides virtual mouse positions.
Locked
```
