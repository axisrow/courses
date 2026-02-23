---
title: "API 集成"
weight: 11
bookToc: true
---

# API 集成

## 什么是 API？

API（应用程序编程接口）是你的应用与其他服务通信的方式。例如获取天气数据、处理支付或发送邮件。

把 API 想象成餐厅服务员——你告诉服务员你想要什么（请求），他从厨房带给你（响应）。

## v0 中的 API

v0 可以自动集成流行的工具和 API：

- 很多集成不需要单独注册账号
- AI 理解常见的 API 模式
- 你可以用普通语言描述需要什么数据

## 如何添加 API 集成

在提示词中描述即可：

- "Create a weather widget that shows the current weather for Beijing"
- "Build a contact form that sends emails via Resend"
- "Make a page that displays the latest news from an RSS feed"

v0 会生成包含必要 API 调用的代码。

## 流行的集成

| 服务 | 用途 |
|------|------|
| Stripe | 支付处理 |
| Resend | 发送邮件 |
| OpenAI | AI 文本生成 |
| Supabase | 数据库和认证 |
| Cloudinary | 图片管理 |

## API 密钥

一些 API 需要密钥（像密码一样）：

1. 在 API 服务注册
2. 从控制面板获取 API 密钥
3. 添加到 Vercel 的环境变量中
4. 永远不要把 API 密钥直接写在代码里

## 总结

API 让你的应用连接外部服务。v0 让集成变得简单——只需描述你需要什么。下一课——使用数据库。
