---
title: "你的第一个合成"
weight: 3
bookToc: true
---

# 你的第一个合成

Remotion 已安装好，让我们了解视频是如何构建的。

## 什么是合成？

合成是视频的蓝图，它定义了：
- **宽度**和**高度**（像素）——视频分辨率
- **FPS**（每秒帧数）——视频流畅度
- **时长**（帧数）——视频长度

例如：1920×1080，30 fps，150帧 = 5秒的全高清视频。

## 查看代码

打开项目中的 `src/Root.tsx`：

```tsx
import { Composition } from "remotion";
import { MyComposition } from "./MyComposition";

export const RemotionRoot = () => {
  return (
    <Composition
      id="MyVideo"
      component={MyComposition}
      durationInFrames={150}
      fps={30}
      width={1920}
      height={1080}
    />
  );
};
```

## 理解每个部分

| 属性 | 作用 |
|---|---|
| `id` | 视频名称 |
| `component` | 绘制视频的 React 组件 |
| `durationInFrames` | 总帧数 |
| `fps` | 每秒帧数 |
| `width` / `height` | 视频分辨率 |

## 自己试试

1. 将 `durationInFrames` 改为 `300`（现在是10秒）
2. 保存文件
3. 预览会自动更新

## 总结

合成定义了视频的尺寸、速度和长度，它连接到一个绘制每帧的 React 组件。
