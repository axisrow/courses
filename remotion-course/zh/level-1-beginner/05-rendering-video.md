---
title: "渲染你的视频"
weight: 5
bookToc: true
---

# 渲染你的视频

你一直在浏览器中预览视频。现在让我们把它变成真正的视频文件。

## 什么是渲染？

渲染是将代码转换为视频文件（如 MP4）的过程。Remotion 对每一帧截图，然后将它们拼接在一起。

## 从命令行渲染

在项目文件夹中运行：

```bash
npx remotion render MyVideo out/video.mp4
```

- `MyVideo` —— `Root.tsx` 中的合成 ID
- `out/video.mp4` —— 保存位置

这可能需要几分钟。

## 从 Studio 渲染

你也可以在 Remotion Studio（浏览器预览）中点击 **Render** 按钮，通过可视界面选择格式、质量等。

## 输出格式

| 格式 | 用途 |
|---|---|
| MP4 | 最常用，到处都能播放 |
| WebM | 文件更小，适合网页 |
| GIF | 短循环，社交媒体 |
| PNG 序列 | 单独帧，用于后期处理 |

## 加速渲染的技巧

- 关闭其他程序以释放 CPU
- 测试时使用较低分辨率
- Remotion 会自动使用多个 CPU 核心

## 总结

渲染将代码转换为真正的视频文件。使用命令行或 Studio 界面。
