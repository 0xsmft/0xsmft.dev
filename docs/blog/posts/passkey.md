---
date: 2026-08-04
categories:
  - C++
authors:
  - 0xsmft
slug: cpp
description: >
  Passkey idiom
---

# Passkey

Last Updated: 08 August 2026

We've all run into this issue before, we want to give access to certain functions of a class, so we simply make it a friend class then you realise that maybe this class should have access to all of the original classes' privates, so what do we do? Normally, I would create a public function and just hope nobody else in the codebase will call it. However, there is a better way, enter the passkey idiom, a somewhat forgotten idiom.

## The benefits

The main benefits of the passkey is that befriending a class means that the befriend class will have access to all of the classes' privates, in some cases this is what we want but sometimes this is what we want to avoid. A passkey will help restrict certain functions so that only the allowed class can ever call the function.

## Implementation

```cpp
template<typename Ty>
class Passkey
{
private:
  Passkey() = default;
  Passkey( const Passkey& ) = default;
  ~Passkey() = default;

private:
  friend Ty;
};
```

By having a private copy constructor we disable the use of something like this:
```cpp
Passkey<MyOtherClass>* pPassKey = nullptr;
MyFunction( *pPassKey );
```
As this will fail to compile.

### Usage

```cpp
MyFunction( Passkey<MyOtherClass>() );
```

## Conclusion

As we can see this helps solve our problem, we’ve solved the friendship issue as only the class specified in the passkey template argument can call the function.

## Reference

My inspiration for creating a passkey came from fellow programmer [Nathan Baggs](https://www.youtube.com/@nathanbaggs) on a live stream of him speaking about the same issue.
