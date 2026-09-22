# RubyWindowSpecification

``#include "Saturn/Core/Ruby/RubyCore.h"``

Creation values for a RubyWindow.

```cpp
struct RubyWindowSpecification.
```

## Members

```cpp
std::wstring_view Name;
uint32_t Width = 0;
uint32_t Height = 0;
RubyGraphicsAPI GraphicsAPI = RubyGraphicsAPI::None;
RubyStyle Style = RubyStyle::Default;
bool ShowNow = true;
RubyWindow* pParentWindow = nullptr;
```
