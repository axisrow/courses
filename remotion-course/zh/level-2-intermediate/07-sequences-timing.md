---
title: "序列与时间控制"
weight: 7
bookToc: true
---

# 序列与时间控制

真正的视频有多个场景。Remotion 的 `<Sequence>` 组件让你在时间线上安排它们。

## 什么是序列？

序列是视频中从特定帧开始的一个部分。把它想象成在时间线上放置片段。

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

## 序列如何工作

- `from`：序列开始的帧
- `durationInFrames`：持续多久（可选——省略则持续到结尾）
- 在序列内部，`useCurrentFrame()` 会重置为 0

这很强大！每个场景的动画都从0开始，你可以独立构建场景。

## 命名序列

添加 `name` 属性使 Studio 时间线更清晰：

```tsx
<Sequence name="标题画面" from={0} durationInFrames={60}>
```

## 重叠序列

序列可以重叠——适用于转场：

```tsx
<Sequence from={0} durationInFrames={60}>
  <Scene1 />
</Sequence>
<Sequence from={50} durationInFrames={60}>
  <Scene2 />
</Sequence>
```

第50-59帧同时显示两个场景。

## 总结

序列将视频组织成定时部分。每个序列都有自己的本地时间线。
