# RubyKey

High level, hardware-independent, backend-independent and layout-independent key codes.

```cpp
using KeyCode = uint16_t;

enum RubyKey : KeyCode
```

Although the key codes are layout-independent the available keys are based off the English US QWERTY layout.

## Valid flags

```cpp
//////////////////////////////////////////////////////////////////////////
// Undefined key

RubyKey_UnknownKey = 0,

//////////////////////////////////////////////////////////////////////////
// Modifier keys

RubyKey_LeftShift,
RubyKey_RightShift,
RubyKey_LeftCtrl,
RubyKey_RightCtrl,
RubyKey_LeftAlt,
RubyKey_RightAlt,
RubyKey_OSKey,
RubyKey_OSKeyRight,

//////////////////////////////////////////////////////////////////////////
// Lock keys

RubyKey_CapsLock,
RubyKey_NumLock,
RubyKey_ScrollLock,

//////////////////////////////////////////////////////////////////////////
// Function keys

RubyKey_F1, RubyKey_F2, RubyKey_F3, RubyKey_F4, RubyKey_F5, RubyKey_F6,
RubyKey_F7, RubyKey_F8, RubyKey_F9, RubyKey_F10, RubyKey_F11, RubyKey_F12,

//////////////////////////////////////////////////////////////////////////
// Printable keys

RubyKey_A, RubyKey_B, RubyKey_C, RubyKey_D, RubyKey_E, RubyKey_F, RubyKey_G,
RubyKey_H, RubyKey_I, RubyKey_J, RubyKey_K, RubyKey_L, RubyKey_M, RubyKey_N,
RubyKey_O, RubyKey_P, RubyKey_Q, RubyKey_R, RubyKey_S, RubyKey_T, RubyKey_U,
RubyKey_V, RubyKey_W, RubyKey_X, RubyKey_Y, RubyKey_Z,


//////////////////////////////////////////////////////////////////////////
// Numerical keys
RubyKey_Num0, RubyKey_Num1, RubyKey_Num2, RubyKey_Num3, RubyKey_Num4,
RubyKey_Num5, RubyKey_Num6, RubyKey_Num7, RubyKey_Num8, RubyKey_Num9,

//////////////////////////////////////////////////////////////////////////
// Grammar / symbols

RubyKey_Space,
RubyKey_Apostrophe,
RubyKey_Hash, // UK Only
RubyKey_Comma,
RubyKey_Minus,
RubyKey_Period,
RubyKey_Slash,
RubyKey_Semicolon,
RubyKey_Equal,
RubyKey_LeftBracket,
RubyKey_Backslash,   
RubyKey_RightBracket,
RubyKey_Grave,          // `

//////////////////////////////////////////////////////////////////////////
// Navigation / editing

RubyKey_Esc,
RubyKey_Enter,
RubyKey_Tab,
RubyKey_Backspace,
RubyKey_Insert,
RubyKey_Delete,
RubyKey_Home,
RubyKey_End,
RubyKey_PageUp,
RubyKey_PageDown,

//////////////////////////////////////////////////////////////////////////
// Arrows

RubyKey_UpArrow,
RubyKey_DownArrow,
RubyKey_LeftArrow,
RubyKey_RightArrow,

//////////////////////////////////////////////////////////////////////////
// Numpad

RubyKey_Numpad0,
RubyKey_Numpad1,
RubyKey_Numpad2,
RubyKey_Numpad3,
RubyKey_Numpad4,
RubyKey_Numpad5,
RubyKey_Numpad6,
RubyKey_Numpad7,
RubyKey_Numpad8,
RubyKey_Numpad9,
RubyKey_NumpadDecimal,
RubyKey_NumpadAdd,
RubyKey_NumpadSubtract,
RubyKey_NumpadMultiply,
RubyKey_NumpadDivide,
RubyKey_NumpadEnter,

//////////////////////////////////////////////////////////////////////////
// AUX

RubyKey_PrintScreen,
RubyKey_Pause,
RubyKey_Menu,

RubyKey_EnumSize
```
