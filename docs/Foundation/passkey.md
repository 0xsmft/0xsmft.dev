# Passkey

`#include "Saturn/Core/Passkey.h"`

A passkey helps restrict certain functions to certain classes, allowing that only class "Ty" can use the function.

```cpp
template<typename Ty>
class Passkey
```

This helps us avoid using "friend class Ty" in the class itself because friend classes are an "all or nothing" solution.

## Public members

There are no public members.

## Usage

```cpp
void MyClass::DoSomeShit( Passkey<MyOtherClass> pk ) 
{
    ...code...
}

// And use as such:
m_pMyClass->DoSomeShit( Passkey<MyOtherClass>() );
```
