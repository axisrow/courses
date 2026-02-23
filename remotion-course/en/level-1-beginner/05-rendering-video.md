---
title: "Rendering Your Video"
weight: 5
bookToc: true
---

# Rendering Your Video

You've been previewing your video in the browser. Now let's turn it into an actual video file.

## What Is Rendering?

Rendering is the process of converting your code into a video file (like MP4). Remotion takes a screenshot of every frame and stitches them together.

## Rendering from the Command Line

In your project folder, run:

```bash
npx remotion render MyVideo out/video.mp4
```

- `MyVideo` — the composition ID from your `Root.tsx`
- `out/video.mp4` — where to save the file

This may take a few minutes depending on your video's length and complexity.

## Rendering from the Studio

You can also click the **Render** button in the Remotion Studio (the browser preview). It gives you a visual interface to choose format, quality, and more.

## Output Formats

| Format | Use Case |
|---|---|
| MP4 | Most common, works everywhere |
| WebM | Smaller files, good for web |
| GIF | Short loops, social media |
| PNG sequence | Individual frames for post-processing |

## Tips for Faster Rendering

- Close other programs to free up CPU
- Use a lower resolution for testing
- Remotion uses multiple CPU cores automatically

## Summary

Rendering converts your code into a real video file. Use the command line or the Studio interface.
