---
title: "Server-Side Rendering with Remotion Lambda"
weight: 12
bookToc: true
---

# Server-Side Rendering with Remotion Lambda

Remotion Lambda lets you render videos in the cloud using AWS Lambda, enabling massive parallelism.

## Why Lambda?

- **Speed**: Render a 5-minute video in seconds by splitting it across many functions
- **Scale**: Render thousands of videos simultaneously
- **Cost**: Pay only for compute time used

## How It Works

1. Your video code is bundled and uploaded to S3
2. A Lambda function is invoked for each chunk of frames
3. Chunks are stitched together into the final video
4. The result is saved to S3

## Setup Overview

```bash
npx remotion lambda policies role
npx remotion lambda sites create src/index.ts
npx remotion lambda functions deploy
```

## Rendering via CLI

```bash
npx remotion lambda render \
  <site-url> \
  MyVideo \
  --props='{"name": "Alice"}'
```

## Rendering via API

```tsx
import { renderMediaOnLambda } from "@remotion/lambda/client";

const result = await renderMediaOnLambda({
  region: "us-east-1",
  functionName: "remotion-render",
  serveUrl: siteUrl,
  composition: "MyVideo",
  inputProps: { name: "Alice" },
  codec: "h264",
});

console.log(result.outputUrl);
```

## Cost Optimization

- Use smaller resolutions for drafts
- Set appropriate memory (1769 MB is a good default)
- Delete old sites and functions regularly

## Alternatives

Remotion also supports:
- **Cloud Run** (Google Cloud)
- **Custom servers** with `@remotion/renderer`

## Summary

Remotion Lambda splits rendering across many AWS Lambda functions for speed and scale. Set up once, render thousands of videos via CLI or API.
