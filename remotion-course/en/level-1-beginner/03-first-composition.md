---
title: "Your First Composition"
weight: 3
bookToc: true
---

# Your First Composition

Now that Remotion is installed, let's understand how a video is built.

## What Is a Composition?

A composition is your video's blueprint. It defines:
- **Width** and **Height** (in pixels) — the video resolution
- **FPS** (frames per second) — how smooth the video looks
- **Duration** (in frames) — how long the video is

For example: 1920×1080, 30 fps, 150 frames = a 5-second Full HD video.

## Looking at the Code

Open `src/Root.tsx` in your project. You'll see something like:

```tsx
import { Composition } from "remotion";
import { MyComposition } from "./MyComposition";

export const RemotionRoot = () => {
  return (
    <Composition
      id="MyVideo"
      component={MyComposition}
      durationInFrames={150}
      fps={30}
      width={1920}
      height={1080}
    />
  );
};
```

## Understanding Each Part

| Property | What It Does |
|---|---|
| `id` | A name for your video |
| `component` | The React component that draws your video |
| `durationInFrames` | Total number of frames |
| `fps` | Frames per second |
| `width` / `height` | Video resolution |

## Try It Yourself

1. Change `durationInFrames` to `300` (now it's 10 seconds)
2. Save the file
3. Watch the preview update automatically

## Summary

A composition defines your video's size, speed, and length. It connects to a React component that draws each frame.
