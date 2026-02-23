---
title: "Data-Driven Videos"
weight: 11
bookToc: true
---

# Data-Driven Videos

Advanced Remotion projects often pull data from APIs and databases to generate videos automatically.

## Fetching Data

Use `calculateMetadata()` to fetch data before rendering:

```tsx
import { CalculateMetadataFunction } from "remotion";

const calculateMetadata: CalculateMetadataFunction<Props> = async () => {
  const response = await fetch("https://api.example.com/data");
  const data = await response.json();

  return {
    props: { data },
    durationInFrames: data.items.length * 30,
  };
};
```

## Dynamic Duration

Notice how the duration depends on the data. If you have 10 items at 30 frames each, the video is 300 frames long.

## Using delayRender

For data fetching inside components, use `delayRender()`:

```tsx
import { delayRender, continueRender } from "remotion";

const [data, setData] = useState(null);
const [handle] = useState(() => delayRender());

useEffect(() => {
  fetch("https://api.example.com/stats")
    .then((r) => r.json())
    .then((d) => {
      setData(d);
      continueRender(handle);
    });
}, [handle]);
```

`delayRender()` tells Remotion: "Wait, I'm not ready yet." When data arrives, `continueRender()` says: "OK, go ahead."

## Real-World Examples

- **GitHub Unwrapped**: generates year-in-review videos from GitHub data
- **Sales dashboards**: weekly video reports from database queries
- **Social media**: auto-generated highlight reels

## Error Handling

Always handle errors to avoid stuck renders:

```tsx
fetch(url)
  .then(...)
  .catch((err) => {
    cancelRender(err);
  });
```

## Summary

Use `calculateMetadata()` for pre-render data fetching and `delayRender()`/`continueRender()` for in-component fetching. Always handle errors.
