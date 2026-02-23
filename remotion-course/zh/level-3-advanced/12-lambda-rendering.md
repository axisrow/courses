---
title: "使用 Remotion Lambda 进行服务端渲染"
weight: 12
bookToc: true
---

# 使用 Remotion Lambda 进行服务端渲染

Remotion Lambda 让你在 AWS 云端渲染视频，实现大规模并行处理。

## 为什么用 Lambda？

- **速度**：将5分钟视频分割到多个函数，几秒内完成渲染
- **规模**：同时渲染数千个视频
- **成本**：只为使用的计算时间付费

## 工作原理

1. 视频代码打包上传到 S3
2. 为每个帧块调用 Lambda 函数
3. 帧块拼接成最终视频
4. 结果保存到 S3

## 设置概览

```bash
npx remotion lambda policies role
npx remotion lambda sites create src/index.ts
npx remotion lambda functions deploy
```

## 通过 CLI 渲染

```bash
npx remotion lambda render \
  <site-url> \
  MyVideo \
  --props='{"name": "Alice"}'
```

## 通过 API 渲染

```tsx
import { renderMediaOnLambda } from "@remotion/lambda/client";

const result = await renderMediaOnLambda({
  region: "us-east-1",
  functionName: "remotion-render",
  serveUrl: siteUrl,
  composition: "MyVideo",
  inputProps: { name: "Alice" },
  codec: "h264",
});

console.log(result.outputUrl);
```

## 成本优化

- 草稿使用较低分辨率
- 设置合适的内存（1769 MB 是不错的默认值）
- 定期删除旧的站点和函数

## 替代方案

Remotion 还支持：
- **Cloud Run**（Google Cloud）
- **自定义服务器**（使用 `@remotion/renderer`）

## 总结

Remotion Lambda 将渲染分布到多个 AWS Lambda 函数，实现速度和规模。一次设置，通过 CLI 或 API 渲染数千个视频。
