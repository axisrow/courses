---
title: "Sequences and Timing"
weight: 7
bookToc: true
---

# Sequences and Timing

Real videos have multiple scenes. Remotion's `<Sequence>` component lets you arrange them on a timeline.

## What Is a Sequence?

A Sequence is a section of your video that starts at a specific frame. Think of it as placing clips on a timeline.

```tsx
import { Sequence } from "remotion";

export const MyVideo = () => {
  return (
    <>
      <Sequence from={0} durationInFrames={60}>
        <TitleScreen />
      </Sequence>
      <Sequence from={60} durationInFrames={90}>
        <MainContent />
      </Sequence>
      <Sequence from={150} durationInFrames={60}>
        <EndScreen />
      </Sequence>
    </>
  );
};
```

## How Sequences Work

- `from`: the frame where this sequence starts
- `durationInFrames`: how long it lasts (optional — omit for "until the end")
- Inside a Sequence, `useCurrentFrame()` resets to 0

This reset is powerful! Each scene's animations start from 0, so you can build scenes independently.

## Naming Sequences

Add a `name` prop for clarity in the Studio timeline:

```tsx
<Sequence name="Title Screen" from={0} durationInFrames={60}>
```

## Overlapping Sequences

Sequences can overlap — useful for transitions:

```tsx
<Sequence from={0} durationInFrames={60}>
  <Scene1 />
</Sequence>
<Sequence from={50} durationInFrames={60}>
  <Scene2 />
</Sequence>
```

Frames 50-59 show both scenes simultaneously.

## Summary

Sequences organize your video into timed sections. Each sequence gets its own local timeline.
