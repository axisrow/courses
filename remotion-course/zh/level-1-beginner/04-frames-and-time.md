---
title: "帧与时间"
weight: 4
bookToc: true
---

# 帧与时间

每个视频都是一系列快速播放的静态图片。Remotion 让你控制每一帧。

## 什么是帧？

帧是一张静态图片。当许多帧快速连续显示时（像翻页书），你就看到了运动。

## useCurrentFrame 钩子

Remotion 提供了 `useCurrentFrame()` 函数，它告诉组件当前显示的是哪一帧。

```tsx
import { useCurrentFrame } from "remotion";

export const Counter = () => {
  const frame = useCurrentFrame();
  return (
    <div style={{ fontSize: 80, textAlign: "center" }}>
      帧: {frame}
    </div>
  );
};
```

在 30 fps 下，计数器在5秒内从0数到149。

## 将帧转换为秒

公式很简单：

```
秒 = 帧 / fps
```

30 fps 时，第90帧 = 视频的第3秒。

## useVideoConfig 钩子

在组件内获取视频设置：

```tsx
import { useVideoConfig } from "remotion";

const { fps, width, height, durationInFrames } = useVideoConfig();
```

## 自己试试

创建一个进度条组件，随视频播放而填充：

```tsx
const frame = useCurrentFrame();
const { durationInFrames } = useVideoConfig();
const progress = frame / durationInFrames;
```

## 总结

帧是视频的构建块。`useCurrentFrame()` 告诉你当前帧，`useVideoConfig()` 提供视频属性。
