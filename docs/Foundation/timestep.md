# Timestep

Tracks the amount of time has passed since the last frame (i.e. delta time).

```cpp
class Timestep
```

## Public members

```cpp
Timestep() = default;
Timestep( float time );

inline float Seconds() const;
inline float Milliseconds() const;

// Returns time in seconds.
operator float() { return m_Time; }
```
