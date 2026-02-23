---
title: "自定义组件与复用"
weight: 13
bookToc: true
---

# 自定义组件与复用

随着项目增长，你需要组织良好、可复用的组件。

## 组件架构

这样组织你的项目：

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

## 构建可复用的 Fade 组件

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

## 使用组件

```tsx
<Sequence from={0} durationInFrames={60}>
  <Fade>
    <Title text="欢迎" />
  </Fade>
</Sequence>
```

## AbsoluteFill 层叠

```tsx
import { AbsoluteFill } from "remotion";

export const Scene = () => (
  <AbsoluteFill>
    <AbsoluteFill style={{ backgroundColor: "black" }} />
    <AbsoluteFill style={{ justifyContent: "center", alignItems: "center" }}>
      <h1>你好</h1>
    </AbsoluteFill>
  </AbsoluteFill>
);
```

多个 `AbsoluteFill` 层层叠加。

## 技巧

- 组件只做一件事
- 接受 props 进行自定义
- 使用 TypeScript 确保类型安全
- 将魔法数字提取为常量

## 总结

构建带 props 的可复用组件，按用途组织文件，使用 `AbsoluteFill` 进行层叠。
