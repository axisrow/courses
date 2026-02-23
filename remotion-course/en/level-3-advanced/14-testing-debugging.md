---
title: "Testing and Debugging"
weight: 14
bookToc: true
---

# Testing and Debugging

Professional video projects need testing and debugging strategies. Remotion provides tools to help.

## Visual Testing in the Studio

The Remotion Studio is your primary debugging tool:
- Scrub through frames to check animations
- Use the timeline to verify sequence timing
- Check different resolutions with the zoom controls

## Console Logging

Add `console.log()` in your components — output appears in the browser console:

```tsx
const frame = useCurrentFrame();
console.log("Current frame:", frame);
```

## Common Issues and Fixes

### Flickering

**Problem**: Images or content flash during rendering.
**Solution**: Use `<Img>` instead of `<img>`, and `delayRender()` for async data.

### Audio Out of Sync

**Problem**: Audio doesn't match visuals.
**Solution**: Check that audio starts at the correct frame within sequences.

### Slow Rendering

**Problem**: Rendering takes too long.
**Solution**:
- Simplify complex CSS
- Reduce API calls
- Use `getStaticFiles()` instead of fetching

## Snapshot Testing

```tsx
import { renderFrames } from "@remotion/renderer";

// Render specific frames for comparison
await renderFrames({
  composition,
  onFrameUpdate: (frame) => console.log(`Frame ${frame}`),
  outputDir: "./test-frames",
  imageFormat: "png",
});
```

## The Remotion Studio Inspector

Click on any element in the Studio to inspect its properties, position, and timing.

## Tips

- Test at the beginning, middle, and end of your video
- Check edge cases (frame 0, last frame)
- Test with different props values
- Render a low-res version before final render

## Summary

Use the Studio for visual debugging, console logs for data debugging, and test edge cases to catch issues early.
