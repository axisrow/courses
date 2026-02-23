---
title: "架构概览"
weight: 2
bookToc: true
---

# 架构概览

## 整体结构

Sentient 由两个主要部分组成：

1. **客户端（前端）** — 基于 Next.js 的 Web 应用。这是你在浏览器中看到和操作的界面。
2. **服务器（后端）** — 基于 Python FastAPI 的应用。这是处理消息、与 AI 模型通信、连接外部服务的"大脑"。

## 支撑服务

| 服务 | 作用 |
|---|---|
| **Redis** | 快速缓存和后台任务的消息代理。 |
| **PostgreSQL + pgvector** | 存储结构化数据和用于记忆搜索的向量嵌入。 |
| **ChromaDB** | 用于语义搜索的轻量级向量数据库。 |
| **LiteLLM** | 代理层，让 Sentient 可以使用多种 AI 模型（OpenAI、Gemini、Ollama 等）。 |
| **Celery Workers** | 执行后台和定时任务。 |

## 消息流转过程

1. 你在 Web 界面输入消息。
2. 客户端通过 WebSocket 将消息发送到服务器。
3. 服务器检查你的记忆和上下文，然后通过 LiteLLM 发送给 AI 模型。
4. AI 模型回复。如果需要使用工具（如查看日历），服务器会调用相应的 **MCP 服务器**。
5. 最终回复通过 WebSocket 返回浏览器。

## MCP Hub — 集成层

MCP（Model Context Protocol）是连接外部应用的标准。每个 MCP 服务器负责一个具体服务的认证和通信。

## 小结

Sentient = **Web 界面** + **Python API 服务器** + **数据库** + **AI 模型** + **MCP 集成**。理解这些模块将帮助你学习后续课程。
