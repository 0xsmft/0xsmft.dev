# RubyMouseButton

`#include "Saturn/Core/Ruby/RubyEventType.h"`

High level, hardware-independent and backend-independent mouse button codes.

```cpp
enum RubyMouseButton : uint8_t
```

## Valid flages

```cpp
RubyMouseButton_Left   = 0,
RubyMouseButton_Right  = 1,
RubyMouseButton_Middle = 2,
RubyMouseButton_Extra1 = 3,
RubyMouseButton_Extra2 = 4,

RubyMouseButton_Unknown = 6,
RubyMouseButton_EnumSize = RubyMouseButton_Unknown - 1,
```
