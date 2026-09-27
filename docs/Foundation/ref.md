# Ref

``#include "Saturn/Core/Ref.h"``

Ref is an intrusive, thread safe, shared ownership, reference counted, authoritative smart pointer similar to std::shared_ptr Intrusive refs do not support the usage of WeakRefs, you must use SharedPtr for that!

```cpp
template<typename T>
class Ref final
```

Refs take up less space than SharedPtrs, as the Ref class it self only needs 8 bytes (on 64 bit machines) for the pointer and then T needs an additional 4 bytes (excl. vtable) for the reference count bringing it to a total of 12 bytes but only 8 bytes per ref!

**NB: Any class that must use Ref must be a child of RefTarget**

## Public members

```cpp
Ref();
Ref( std::nullptr_t );
Ref( T* pointer );

template<typename T2>
Ref( const Ref<T2>& other );

Ref( const Ref<T>& other );

template<typename T2>
Ref( Ref<T2>&& other );

~Ref();

void Reset();

template<typename... VaArgs>
[[nodiscard]] static Ref<T> Create( VaArgs&&... args );

Ref& operator=( std::nullptr_t );

Ref& operator=( Ref<T>& other );

template<typename T2>
Ref& operator=( Ref<T2>& other );

Ref& operator=( const Ref<T>& other );

template<typename T2>
Ref& operator=( const Ref<T2>& other );

template<typename T2>
Ref& operator=( Ref<T2>&& other );

//////////////////////////////////////////////////////////////////////////

operator bool()       { return m_Pointer != nullptr; }
operator bool() const { return m_Pointer != nullptr; }

bool operator ==( const Ref<T>& rOther ) const { return m_Pointer == rOther.m_Pointer; }
bool operator !=( const Ref<T>& rOther ) const { return m_Pointer != rOther.m_Pointer; }

T* operator->()             { return m_Pointer; }
const T* operator->() const { return m_Pointer; }

T& operator*()             { return *m_Pointer; }
const T& operator*() const { return *m_Pointer; }

T* Get()             { return m_Pointer; }
const T* Get() const { return m_Pointer; }

template <typename T2>
[[nodiscard]] Ref<T2> As() const;
```