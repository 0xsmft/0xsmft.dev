---
date: 2026-11-09 
categories:
  - Game Programming
authors:
  - 0xsmft
slug: game_programming
description: >
  Camera shake maths and implmentation.
---

# Camera Shake

Last update: Nov. 9 2026

## Motivation

One of the best effects in a game that helps add another level of realism is the simple camera shake. Whenever it comes to a camera shake I always think about one series of games and that is Rockstar Games' Grand Theft Auto. Even prior to GTA 5, Rockstar Games used the camera shake effect, in the first 3D game in the Grand Theft Auto series (GTA3) there is camera shake whenever an explosion happens. I remember this being one of the first effects that made any game feel more realistic.


## General Idea

In 3D there are two main types of camera shake methods, translational and rotational. Using Translational is where the camera shake is applied to the position of the camera, in theory this may sound good but this causes the camera to be flung about and could even cause the camera to clip into objects, which is not what we want. However, rotational is where the camera shake is applied to the rotation matrix of the camera and it by far the best method for this, it removes the chance of the camera clipping other objects and it also looks much nicer.

Now that we **will** be using a rotational method for camera shake we first need to maintain a trauma level, this is clamped between 0.0…1.0. Trauma can be thought of as a percentage that you add to whenever something happens, for example a small explosion may only add 20% trauma but a huge explosion may add 75%. Trauma is always decaying linearly over time, at a rate which can be fixed or dynamic.

## Code example

Here is my implementation that is used in [Saturn](https://github.com/0xsmft/Saturn-Engine)

```cpp
class CameraShake 
{
public:
  float m_Trauma = 0.0f;
  float m_CurrentTrauma = 0.0f;
  float m_DecaySpeed = 0.0f;

  float m_MaxPitchRad = 0.0f;
  float m_MaxYawRad = 0.0f;
  float m_MaxRollRad = 0.0f;

public:
  glm::quat Tick( Timestep ts );
};

// Tick
glm::quat CameraShake::Tick( Timestep ts ) 
{
  // Decay trauma over time, making sure it doesn't go below 0
  m_CurrentTrauma = glm::max( 0.0f, m_CurrentTrauma - m_DecaySpeed * ts.Seconds() );
 
  // Camera shake is trauma squared.
  const float shake = m_CurrentTrauma * m_CurrentTrauma;
  const float pitchOffset = m_MaxPitchRad * shake * RandValue();
  const float yawOffset = m_MaxYawRad * shake * RandValue();
  const float rollOffset = m_MaxRollRad * shake * RandValue();

  const glm::vec3 angles( glm::radians( pitchOffset ), glm::radians( yawOffset ), glm::radians( rollOffset ) );
  return glm::quat( angles );
}

```

In my implementation I’ve added some extra control for making sure that the camera's max angle doesn't go too far, this is optional and can be omitted. A further improvement that you could add is a function that can increase the trauma.

## Applying this to a camera view matrix

Now that we have calculated the camera shake matrix we still have to actually apply this to a camera.

```cpp
const glm::quat shakeRotMatrix = glm::mat4_cast( /* value from Tick() */ );

// viewMatrix comes from your camera…
viewMatrix *= shakeRotMatrix;
```

## References

Many thanks to this GDC talk [“Math for Game Programmers: Juicing Your Cameras With Math”](https://youtu.be/tu-Qe66AvtY) by Squirrel Eiserloh.

Many thanks to this [blog post](https://jonny.morrill.me/en/blog/gamedev-how-to-implement-a-camera-shake-effect/) by Jonny Morril.

Many thanks to this [Bevy example](https://bevy.org/examples/camera/2d-screen-shake/).

## Extra

My implementation in full can be found [here](https://github.com/0xsmft/Saturn-Engine/blob/vulkan/Saturn/src/Saturn/CameraShake/CameraShakeInstance.cpp).
