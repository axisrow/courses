---
title: "使用 interpolate() 制作动画"
weight: 6
bookToc: true
---

# 使用 interpolate() 制作动画

动画让你的视频栩栩如生。Remotion 的 `interpolate()` 函数是创建流畅运动的主要工具。

## 什么是插值？

插值意味着计算两个点之间的值。例如，在30帧内将一个对象从位置0移动到位置100。

## interpolate 函数

```tsx
import { interpolate, useCurrentFrame } from "remotion";

export const FadeIn = () => {
  const frame = useCurrentFrame();
  const opacity = interpolate(frame, [0, 30], [0, 1]);

  return (
    <div style={{ opacity, fontSize: 80 }}>
      你好世界
    </div>
  );
};
```

文字在30帧内淡入（30 fps 下为1秒）。

## 工作原理

`interpolate(值, 输入范围, 输出范围)`

- **值**：当前帧
- **输入范围**：动画的起止帧 `[0, 30]`
- **输出范围**：映射到的值 `[0, 1]`

## 限制（Clamping）

默认情况下，超出输入范围的值会继续增长。要阻止这种情况：

```tsx
const opacity = interpolate(frame, [0, 30], [0, 1], {
  extrapolateRight: "clamp",
});
```

## 常见动画

- **淡入**：opacity 从 0 到 1
- **滑入**：translateX 从 -100 到 0
- **放大**：scale 从 0 到 1
- **旋转**：rotate 从 0 到 360

## 总结

`interpolate()` 将帧号映射为动画值，是所有 Remotion 动画的基础。
