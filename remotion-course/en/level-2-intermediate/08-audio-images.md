---
title: "Adding Audio and Images"
weight: 8
bookToc: true
---

# Adding Audio and Images

Videos need more than text. Let's add audio tracks and images to your Remotion projects.

## Adding Images

Place images in the `public` folder of your project, then use them:

```tsx
import { Img, staticFile } from "remotion";

export const MyScene = () => {
  return <Img src={staticFile("photo.jpg")} />;
};
```

`staticFile()` points to files in your `public` folder. Use the `<Img>` component (not HTML `<img>`) — it waits for the image to load before rendering.

## Adding Audio

```tsx
import { Audio, staticFile } from "remotion";

export const MyScene = () => {
  return (
    <>
      <Audio src={staticFile("music.mp3")} />
      <div>Visual content here</div>
    </>
  );
};
```

## Controlling Audio Volume

```tsx
<Audio
  src={staticFile("music.mp3")}
  volume={(f) =>
    interpolate(f, [0, 30], [0, 1], {
      extrapolateRight: "clamp",
    })
  }
/>
```

This fades in the audio over 30 frames.

## Audio with Sequences

Audio inside a `<Sequence>` plays only during that sequence:

```tsx
<Sequence from={60} durationInFrames={120}>
  <Audio src={staticFile("narration.mp3")} />
</Sequence>
```

## Using Remote URLs

You can also use URLs:

```tsx
<Img src="https://example.com/photo.jpg" />
<Audio src="https://example.com/music.mp3" />
```

## Summary

Use `<Img>` for images and `<Audio>` for sound. Both work with local files (via `staticFile()`) and remote URLs.
