---
title: "Parameterized Videos"
weight: 10
bookToc: true
---

# Parameterized Videos

One of Remotion's superpowers is creating different videos from the same template using parameters.

## What Are Input Props?

Input props are data you pass to your video to customize it. Like filling in a form template:

- Name: "Alice" → personalized birthday video for Alice
- Name: "Bob" → same template, different result

## Defining a Schema

```tsx
import { z } from "zod";

const mySchema = z.object({
  name: z.string(),
  color: z.string(),
});
```

## Using Props in Your Composition

```tsx
export const RemotionRoot = () => {
  return (
    <Composition
      id="Greeting"
      component={Greeting}
      schema={mySchema}
      defaultProps={{
        name: "World",
        color: "blue",
      }}
      durationInFrames={150}
      fps={30}
      width={1920}
      height={1080}
    />
  );
};
```

## Accessing Props in Your Component

```tsx
const Greeting: React.FC<z.infer<typeof mySchema>> = ({ name, color }) => {
  return (
    <div style={{ color, fontSize: 80 }}>
      Hello, {name}!
    </div>
  );
};
```

## Rendering with Custom Props

```bash
npx remotion render Greeting out/alice.mp4 \
  --props='{"name": "Alice", "color": "red"}'
```

## Batch Rendering

Combine with a script to render hundreds of personalized videos:

```bash
for name in Alice Bob Charlie; do
  npx remotion render Greeting "out/${name}.mp4" \
    --props="{\"name\": \"${name}\", \"color\": \"blue\"}"
done
```

## Summary

Input props let you create video templates and generate personalized variations. Define a schema, pass props, and render multiple versions.
