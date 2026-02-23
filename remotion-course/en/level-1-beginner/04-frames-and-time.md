---
title: "Frames and Time"
weight: 4
bookToc: true
---

# Frames and Time

Every video is just a series of still images shown very quickly. Remotion gives you control over each one.

## What Is a Frame?

A frame is a single image. When many frames are shown in rapid succession (like a flipbook), you see motion.

## The useCurrentFrame Hook

Remotion provides a special function called `useCurrentFrame()`. It tells your component which frame is currently being displayed.

```tsx
import { useCurrentFrame } from "remotion";

export const Counter = () => {
  const frame = useCurrentFrame();
  return (
    <div style={{ fontSize: 80, textAlign: "center" }}>
      Frame: {frame}
    </div>
  );
};
```

At 30 fps, this counter goes from 0 to 149 over 5 seconds.

## Converting Frames to Seconds

The formula is simple:

```
seconds = frame / fps
```

At 30 fps, frame 90 = 3 seconds into the video.

## The useVideoConfig Hook

To get your video's settings inside a component:

```tsx
import { useVideoConfig } from "remotion";

const { fps, width, height, durationInFrames } = useVideoConfig();
```

## Try It Yourself

Create a component that shows a progress bar that fills up as the video plays:

```tsx
const frame = useCurrentFrame();
const { durationInFrames } = useVideoConfig();
const progress = frame / durationInFrames;
```

## Summary

Frames are the building blocks of video. `useCurrentFrame()` tells you which frame you're on, and `useVideoConfig()` gives you the video's properties.
