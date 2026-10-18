# ActionBindingTriggerState

`#include "Saturn/GameFramework/ActionBinding.h"`

8-bit enum (bitfield).

```cpp
enum class ActionBindingTriggerState : uint8_t
```

The enum allows the [ActionBinding](actingbinding.md) to know when it should fire it's function. Because this is a bitfield you can combine both values.

## Valid bits

| Name | Value |
| ----- | ---- |
| Pressed | 0 |
| Released | 1 |
