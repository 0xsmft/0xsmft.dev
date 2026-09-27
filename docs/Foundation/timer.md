# Timer

`#include "Saturn/Core/Timer.h"`

Although this class is called `Timer`, it's functionality is more that of a stopwatch.

```cpp
class Timer
```

Nanosecond timer, keeping track of a start timestamp and an end timestamp.

Upon creation of a timer the timer will begin.

## Public members

```cpp
void Stop();
void Reset();

float Elapsed();
float ElapsedMilliseconds();
```

*NB: Both `Elapsed` and `ElapsedMilliseconds` return the same value (i.e. milliseconds).*
