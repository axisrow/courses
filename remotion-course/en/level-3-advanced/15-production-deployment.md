---
title: "Production Deployment and Best Practices"
weight: 15
bookToc: true
---

# Production Deployment and Best Practices

You've learned to build videos with Remotion. This final lesson covers deploying to production and best practices.

## Deployment Options

| Option | Best For |
|---|---|
| Remotion Lambda | High volume, serverless |
| Cloud Run | Google Cloud users |
| Self-hosted server | Full control |
| GitHub Actions | CI/CD pipelines |

## Self-Hosted Server Example

```tsx
import { renderMedia, selectComposition } from "@remotion/renderer";
import { bundle } from "@remotion/bundler";

const bundleLocation = await bundle({
  entryPoint: "./src/index.ts",
});

const composition = await selectComposition({
  serveUrl: bundleLocation,
  id: "MyVideo",
});

await renderMedia({
  composition,
  serveUrl: bundleLocation,
  codec: "h264",
  outputLocation: "out/video.mp4",
});
```

## Performance Best Practices

1. **Precompute data** — fetch before rendering, not during
2. **Optimize images** — use WebP, appropriate sizes
3. **Minimize re-renders** — use `React.memo()` for static components
4. **Parallelize** — Lambda splits work across functions
5. **Cache** — reuse bundled sites for multiple renders

## Project Structure Best Practices

- Separate video logic from business logic
- Keep compositions small and focused
- Use a monorepo if building multiple video templates
- Version your templates

## Monitoring

- Track render times and failures
- Set up alerts for failed renders
- Monitor AWS costs if using Lambda

## Security

- Validate input props (Zod schemas help)
- Don't expose render endpoints publicly without auth
- Sanitize user-provided content

## What's Next?

- Explore the [Remotion documentation](https://remotion.dev/docs)
- Join the [Discord community](https://remotion.dev/discord)
- Check the [Showcase](https://remotion.dev/showcase) for inspiration
- Build something amazing! 🎬

## Summary

Choose the right deployment for your needs, follow performance best practices, monitor your renders, and keep learning from the community.
