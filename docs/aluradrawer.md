# Alura Drawer (SAluraDrawer)

Inheritable class to allow for custom drawing onto the AluraCanvas.

This class is pure-virtual and **all** functions must be overridden!

```cpp
class AluraDrawer : public SObject
```

### Functions (public)

```cpp
virtual void OnInit() = 0;
virtual void OnDraw( Timestamp ts ) = 0;
virtual void OnDestroy( Timestamp ts ) = 0;
virtual void OnEvent( Event& rEvent ) = 0;
```

### Notes

`OnInit` is called when the Drawer is pushed back on to the AluraCanvas' drawer list. The same applies for `OnDestroy`.

It's best to not place any initialisation code in the constuctor and place it in the OnInit() function. Same rules applies for OnDestroy().

### SClass Flags

```cpp
Saturn::SC_VisibleInEditor | Saturn::SC_NoExtendedMetadata | Saturn::SC_Abstract;
```

## Related
