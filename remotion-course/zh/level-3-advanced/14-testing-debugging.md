---
title: "测试与调试"
weight: 14
bookToc: true
---

# 测试与调试

专业的视频项目需要测试和调试策略。

## Studio 中的可视化测试

Remotion Studio 是你的主要调试工具：
- 逐帧检查动画
- 使用时间线验证序列时序
- 用缩放控件检查不同分辨率

## 控制台日志

在组件中添加 `console.log()`——输出会显示在浏览器控制台：

```tsx
const frame = useCurrentFrame();
console.log("当前帧:", frame);
```

## 常见问题与解决

### 闪烁

**问题**：图片在渲染时闪烁。
**解决**：使用 `<Img>` 而非 `<img>`，异步数据用 `delayRender()`。

### 音频不同步

**问题**：音频与画面不匹配。
**解决**：检查音频在序列中从正确的帧开始。

### 渲染缓慢

**问题**：渲染时间太长。
**解决**：
- 简化复杂 CSS
- 减少 API 调用
- 使用 `getStaticFiles()` 代替网络请求

## 快照测试

```tsx
import { renderFrames } from "@remotion/renderer";

await renderFrames({
  composition,
  onFrameUpdate: (frame) => console.log(`帧 ${frame}`),
  outputDir: "./test-frames",
  imageFormat: "png",
});
```

## Studio 检查器

点击 Studio 中的任何元素查看其属性和位置。

## 技巧

- 测试视频的开头、中间和结尾
- 检查边界情况（第0帧、最后一帧）
- 用不同参数值测试
- 最终渲染前先渲染低分辨率版本

## 总结

使用 Studio 进行可视化调试，console.log 调试数据，检查边界情况以尽早发现问题。
