---
title: "Spring Animations"
weight: 9
bookToc: true
---

# Spring Animations

Linear animations can feel robotic. Spring animations mimic real-world physics for natural-feeling motion.

## What Is a Spring?

In real life, a spring bounces when released. Remotion's `spring()` function creates similar bouncy, natural motion.

## Basic Spring

```tsx
import { spring, useCurrentFrame, useVideoConfig } from "remotion";

export const BounceIn = () => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();

  const scale = spring({
    frame,
    fps,
    from: 0,
    to: 1,
  });

  return (
    <div style={{ transform: `scale(${scale})` }}>
      🎉
    </div>
  );
};
```

## Spring Configuration

You can tune the spring's behavior:

```tsx
const scale = spring({
  frame,
  fps,
  from: 0,
  to: 1,
  config: {
    damping: 10,    // Less bouncy (higher = less bounce)
    stiffness: 100,  // Speed of movement
    mass: 1,         // Weight of the object
  },
});
```

## Spring vs Interpolate

| Feature | `interpolate()` | `spring()` |
|---|---|---|
| Motion type | Linear | Physics-based |
| Feel | Mechanical | Natural |
| Bounce | No | Yes |
| Duration | Fixed | Automatic |

## Delaying a Spring

```tsx
const scale = spring({
  frame: frame - 30, // Starts at frame 30
  fps,
});
```

## Summary

`spring()` creates natural, bouncy animations. Configure damping, stiffness, and mass to control the feel.
