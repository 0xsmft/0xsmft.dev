# SharedPtr

`#include "Saturn/Core/Ref.h"`

SharedPtr is a reference counted, non-intrusive, thread safe and authoritative smart pointer that works very similar to `std::shared_ptr`.

```cpp
template<typename Ty>
class SharedPtr final
```

The size of this class is 16 bytes however, depending on the control block it may become 24 bytes.

To create a SharedPtr call you may do:
```cpp
SharedPtr<Ty> myPtr = SharedPtr<Ty>::Create(args);
```

## Public members

```cpp
SharedPtr() noexcept = default;
SharedPtr( std::nullptr_t ) noexcept;

// Constructs new control block, assume ownership of pPointer.
explicit SharedPtr( Ty* pPointer );

template<typename Deleter>
SharedPtr( Ty* pPointer, Deleter deleter );

// Copy from SharedPtr with the same type
SharedPtr( const SharedPtr& rOther );

// Copy from SharedPtr a different type
template<typename Ty2>
SharedPtr( const SharedPtr<Ty2>& rOther );

// Move from SharedPtr with the same type
SharedPtr( SharedPtr&& rrOther ) noexcept;

~SharedPtr();

[[nodiscard]] Ty* Get() const;
Ty* operator->() const;
Ty& operator*() const;
operator bool() const;

template <typename T2>
[[nodiscard]] SharedPtr<T2> As() const;

template<typename... VaArgs>
[[nodiscard]] static SharedPtr<Ty> Create( VaArgs&&... rrArgs );

```