---
title: "生产部署与最佳实践"
weight: 15
bookToc: true
---

# 生产部署与最佳实践

你已经学会了用 Remotion 制作视频。最后一课涵盖生产部署和最佳实践。

## 部署选项

| 选项 | 最适合 |
|---|---|
| Remotion Lambda | 大量视频，无服务器 |
| Cloud Run | Google Cloud 用户 |
| 自托管服务器 | 完全控制 |
| GitHub Actions | CI/CD 流水线 |

## 自托管服务器示例

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

## 性能最佳实践

1. **预计算数据** —— 渲染前获取，而非渲染时
2. **优化图片** —— 使用 WebP，合适的尺寸
3. **减少重渲染** —— 静态组件用 `React.memo()`
4. **并行化** —— Lambda 分发工作
5. **缓存** —— 复用打包站点

## 项目结构最佳实践

- 分离视频逻辑和业务逻辑
- 保持合成小而专注
- 多模板用 monorepo
- 为模板做版本管理

## 监控

- 追踪渲染时间和失败
- 设置失败告警
- 使用 Lambda 时监控 AWS 成本

## 安全

- 验证输入参数（Zod schema 很有用）
- 不要公开渲染端点（需要认证）
- 清理用户提供的内容

## 下一步

- 探索 [Remotion 文档](https://remotion.dev/docs)
- 加入 [Discord 社区](https://remotion.dev/discord)
- 查看 [Showcase](https://remotion.dev/showcase) 获取灵感
- 创造精彩作品！🎬

## 总结

选择合适的部署方式，遵循性能最佳实践，监控渲染，持续学习。
