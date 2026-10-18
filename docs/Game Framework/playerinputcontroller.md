# PlayerInputController

`#include "Saturn/GameFramework/PlayerInputController.h"`

The PlayerInputController is the class responsible for managing input bindings from the mouse or keyboard it binds such input events into a function.

```cpp
class PlayerInputController : public RefTarget
```

It is normally used with alongside [Character](character.md) but can be used with any [Entity](../Scene/entity.md).

## Public members

```cpp
using ActionFunction = std::function<void()>;

// Binds an action to a function with a specific trigger state.
//
// @param rBindingName The name of the action binding, this must match with the one in the project settings
// @param state The trigger state of the action.
// @param rFunction The function to execute when the action is triggered.
void BindAction( const std::string& rBindingName, ActionBindingTriggerState state, const ActionFunction& rFunction );

// Removes a previously bound action.
//
// @param rBindingName The name of the action binding, this must match with the one in the project settings
void RemoveAction( const std::string& rBindingName );
```

## Related

[Character](character.md)
[Entity](../Scene/entity.md)
[ActionBinding](actionbinding.md)
