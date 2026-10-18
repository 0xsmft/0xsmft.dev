# ActionBindingData

`#include "Saturn/GameFramework/ActionBinding.h"`

Specification for the real ActionBindings, owned by the Project and only created once.

```cpp
struct ActionBindingData
```

## Public members

```cpp
std::string Name
RubyKey Key;
RubyMouseButton MouseButton;
ActionBindingType Type;

#if !defined(SAT_DIST)
    // The name of the Key/Mouse button
    std::string ActionName;
    // RenderID
    UUID ID;
#endif
```
