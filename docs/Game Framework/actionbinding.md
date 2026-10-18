# ActionBinding

`#include "Saturn/GameFramework/ActionBinding.h"`

An ActionBinding is an key or mouse event that triggers based on certain conditions for example, if the 'A' key is pressed, the project will search for any ActionBinding that matches.

```cpp
struct ActionBinding
```
Unlike [ActionBindingData](actionbindingdata.md), ActionBindings are created and owned by the [PlayerInputController](playerinputcontroller.md).

Think of this as the runtime version of ActionBindingData.

An ActionBinding is defined by it's ActionBindingData.

## Public members

```cpp
RubyKey Key;
RubyMouseButton MouseButton;
ActionBindingType Type;
ActionBindingTriggerState State;

std::function<void()> Function;
```

## Related

[ActionBindingData](actionbindingdata.md)
[PlayerInputController](playerinputcontroller.md)
[ActionBindingType](actionbindingtype.md)
[ActionBindingTriggerState](actionbindingtriggerstate.md)
