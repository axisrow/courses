---
title: "集成与 MCP 服务器"
weight: 6
bookToc: true
---

# 集成与 MCP 服务器

## 什么是 MCP？

MCP（Model Context Protocol）是 Sentient 连接外部服务的方式。每个集成实现为一个小型 MCP 服务器，它负责：

1. 与外部服务进行认证（通常通过 OAuth）。
2. 提供一组 AI 可以调用的**工具**。
3. 将结果返回给 Sentient 主服务器。

## 可用集成

| 类别 | 服务 |
|---|---|
| **Google Workspace** | Gmail、Calendar、Drive、Docs、Sheets、Slides、Tasks、Contacts、Maps |
| **通讯** | Slack、Discord、WhatsApp |
| **生产力** | Notion、Trello、GitHub |
| **信息** | Google Search、News、AccuWeather |
| **工具** | 文件管理、QuickChart、Memory、History |

## 连接集成

1. 在 Sentient 界面打开 **Integrations** 页面。
2. 点击所需服务旁的 **Connect**。
3. 完成 OAuth 授权流程。
4. 连接后，Sentient 可以在对话和任务中使用该服务。

## AI 如何使用集成

当你说"查看我明天的日历"时，AI 会：
1. 识别需要 Google Calendar 工具。
2. 调用 `gcal` MCP 服务器。
3. MCP 服务器使用你的 OAuth 令牌获取事件。
4. 结果返回给 AI，AI 为你格式化展示。

## 编排器

`orchestrator` 模块协调涉及多个工具的复杂工作流——例如读取邮件、创建日历事件、在 Slack 发送摘要。

## 小结

MCP 服务器是 Sentient 与外部世界的桥梁。它们让 Sentient 不仅是聊天机器人，更是一个**能够行动的智能代理**。
