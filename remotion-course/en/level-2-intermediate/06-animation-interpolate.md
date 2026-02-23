---
title: "Animation with interpolate()"
weight: 6
bookToc: true
---

# Animation with interpolate()

Animations make your videos come alive. Remotion's `interpolate()` function is your main tool for creating smooth motion.

## What Is Interpolation?

Interpolation means calculating values between two points. For example, moving an object from position 0 to position 100 over 30 frames.

## The interpolate Function

```tsx
import { interpolate, useCurrentFrame } from "remotion";

export const FadeIn = () => {
  const frame = useCurrentFrame();
  const opacity = interpolate(frame, [0, 30], [0, 1]);

  return (
    <div style={{ opacity, fontSize: 80 }}>
      Hello World
    </div>
  );
};
```

This fades in text over 30 frames (1 second at 30 fps).

## How It Works

`interpolate(value, inputRange, outputRange)`

- **value**: the current frame
- **inputRange**: when the animation starts and ends `[0, 30]`
- **outputRange**: what values to map to `[0, 1]`

## Clamping

By default, values outside the input range keep growing. To stop that:

```tsx
const opacity = interpolate(frame, [0, 30], [0, 1], {
  extrapolateRight: "clamp",
});
```

## Common Animations

- **Fade in**: opacity from 0 to 1
- **Slide in**: translateX from -100 to 0
- **Scale up**: scale from 0 to 1
- **Rotate**: rotate from 0 to 360

## Summary

`interpolate()` maps frame numbers to animation values. It's the foundation of all Remotion animations.
