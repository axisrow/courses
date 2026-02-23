---
title: "DeerFlow架构"
weight: 1
bookToc: true
---

# DeerFlow架构

## 简介

在本课中，我们将"揭开DeerFlow的面纱"，了解系统内部是如何构建的。理解架构有助于您更有效地配置、扩展和调试DeerFlow。

## 整体架构

```
                    ┌──────────────────────────────────────┐
                    │          Nginx（端口2026）             │
                    │            反向代理                    │
                    └───────┬──────────────────┬───────────┘
                            │                  │
          /api/langgraph/*  │                  │  /api/*（其他）
                            ▼                  ▼
           ┌────────────────────┐  ┌────────────────────────┐
           │ LangGraph Server   │  │   Gateway API (8001)   │
           │   （端口2024）      │  │   FastAPI REST         │
           └────────────────────┘  └────────────────────────┘
```

### 组件

| 组件 | 端口 | 技术 | 用途 |
|------|------|------|------|
| **Nginx** | 2026 | Nginx | 反向代理，统一入口 |
| **Frontend** | 3000 | Next.js | Web用户界面 |
| **Gateway API** | 8001 | FastAPI | 模型、MCP、技能、记忆的REST API |
| **LangGraph Server** | 2024 | LangGraph | 智能体执行环境 |

## 主智能体

主智能体由`make_lead_agent(config)`创建，包括：

1. 通过`create_chat_model()`**动态选择模型**
2. 用于请求处理的**中间件链**
3. 通过`get_available_tools()`获取的**工具系统**
4. 包含技能、记忆和指令的**系统提示**

## 中间件链

中间件组件按顺序处理请求，像过滤器一样。每个负责特定任务：

| # | 中间件 | 用途 |
|---|--------|------|
| 1 | **ThreadDataMiddleware** | 为每个线程创建目录 |
| 2 | **UploadsMiddleware** | 将上传的文件注入上下文 |
| 3 | **SandboxMiddleware** | 获取代码执行沙箱 |
| 4 | **DanglingToolCallMiddleware** | 处理未完成的工具调用 |
| 5 | **SummarizationMiddleware** | 接近限制时压缩上下文 |
| 6 | **TodoListMiddleware** | 在计划模式中跟踪任务 |
| 7 | **TitleMiddleware** | 生成对话标题 |
| 8 | **MemoryMiddleware** | 将对话发送到记忆分析 |
| 9 | **ViewImageMiddleware** | 为视觉模型注入图片 |
| 10 | **SubagentLimitMiddleware** | 限制子智能体数量 |
| 11 | **ClarificationMiddleware** | 拦截澄清请求（始终最后） |

## 工具系统

从多个来源收集工具：配置定义、MCP服务器、内置工具和子智能体工具。

## 反射系统

DeerFlow使用**动态模块加载**，允许通过`config.yaml`中的字符串配置组件，无需修改代码。

## 项目结构

```
deer-flow/
├── backend/src/
│   ├── agents/           # 智能体系统
│   ├── gateway/           # REST API
│   ├── sandbox/           # 沙箱系统
│   ├── subagents/         # 子智能体系统
│   ├── tools/             # 内置工具
│   ├── mcp/               # MCP集成
│   ├── models/            # 模型工厂
│   ├── skills/            # 技能系统
│   └── config/            # 配置系统
├── frontend/               # Next.js
├── skills/                 # 技能
└── config.yaml             # 配置
```

## 总结

- DeerFlow建立在4个服务之上：Nginx、Frontend、Gateway API、LangGraph
- 主智能体使用11个中间件组件链
- 工具从配置、MCP、内置和子智能体组装
- 通过反射系统进行动态模块加载
- 每个对话都有隔离的状态（ThreadState）
