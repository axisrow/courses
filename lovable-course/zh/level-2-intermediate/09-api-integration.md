---
title: "API 集成"
weight: 9
bookToc: true
---

# API 集成

将外部服务连接到你的应用。

## 什么是 API？

API 让你的应用与其他服务通信——天气数据、支付、AI 模型等。

## 获取外部数据

> 从公共新闻 API 获取最新新闻，以卡片形式显示。

Lovable 会生成请求逻辑、加载状态和错误处理。

## Edge Functions

需要服务器端逻辑时，使用 Supabase Edge Functions：

> 创建一个 edge function，调用 OpenAI API 并返回文本摘要。

Edge Functions 在服务器端运行，API 密钥安全。

## 环境变量

> 把 API 密钥存储在环境变量中，不要硬编码。

Lovable 使用 Supabase secrets 存储服务器端密钥。

## 常见集成

| 服务 | 用途 |
|------|------|
| Stripe | 支付和订阅 |
| OpenAI | AI 功能 |
| SendGrid | 邮件通知 |
| Cloudinary | 图片上传和处理 |
| Google Maps | 地图和定位 |

## Webhook

> 创建新订单时，发送 webhook 到 Slack 频道。

## 错误处理

> 如果 API 调用失败，显示友好的错误信息。添加重试按钮。

## 总结

API 扩展应用能力。使用 Edge Functions 进行安全的服务器端调用。Lovable 为你处理集成代码。
