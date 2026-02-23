---
title: "Custom Components and Reusability"
weight: 13
bookToc: true
---

# Custom Components and Reusability

As your projects grow, you need well-organized, reusable components. This lesson covers patterns for professional Remotion projects.

## Component Architecture

Organize your project like this:

```
src/
  components/
    Title.tsx
    Subtitle.tsx
    Background.tsx
    Transitions/
      FadeIn.tsx
      SlideIn.tsx
  scenes/
    Intro.tsx
    MainContent.tsx
    Outro.tsx
  Root.tsx
```

## Building a Reusable Fade Component

```tsx
import { interpolate, useCurrentFrame } from "remotion";

type FadeProps = {
  children: React.ReactNode;
  durationInFrames?: number;
  direction?: "in" | "out";
};

export const Fade: React.FC<FadeProps> = ({
  children,
  durationInFrames = 30,
  direction = "in",
}) => {
  const frame = useCurrentFrame();
  const opacity = interpolate(
    frame,
    [0, durationInFrames],
    direction === "in" ? [0, 1] : [1, 0],
    { extrapolateRight: "clamp" }
  );

  return <div style={{ opacity }}>{children}</div>;
};
```

## Using Your Component

```tsx
<Sequence from={0} durationInFrames={60}>
  <Fade>
    <Title text="Welcome" />
  </Fade>
</Sequence>
```

## AbsoluteFill for Layering

```tsx
import { AbsoluteFill } from "remotion";

export const Scene = () => (
  <AbsoluteFill>
    <AbsoluteFill style={{ backgroundColor: "black" }} />
    <AbsoluteFill style={{ justifyContent: "center", alignItems: "center" }}>
      <h1>Hello</h1>
    </AbsoluteFill>
  </AbsoluteFill>
);
```

Multiple `AbsoluteFill` layers stack on top of each other.

## Tips

- Keep components focused on one task
- Accept props for customization
- Use TypeScript for type safety
- Extract magic numbers into constants

## Summary

Build reusable components with props, organize files by purpose, and use `AbsoluteFill` for layering.
