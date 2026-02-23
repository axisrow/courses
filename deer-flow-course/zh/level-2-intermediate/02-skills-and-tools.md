---
title: "技能与工具"
weight: 2
bookToc: true
---

# 技能与工具

## 简介

**技能**和**工具**使DeerFlow真正多才多艺。技能定义智能体*能做什么*，工具定义*如何做*。

## 技能

### 什么是技能？

**技能**是一个包含指令的Markdown文件，描述特定类型任务的逐步过程。可以把它想象成AI智能体的详细工作说明书。

### 内置技能

| 技能 | 说明 |
|------|------|
| `research` | 深度主题研究，附带来源引用 |
| `report-generation` | 创建结构化报告 |
| `slide-creation` | 生成演示文稿 |
| `web-page` | 创建HTML/CSS网页 |
| `image-generation` | 生成图片 |

### 技能存储位置

```
deer-flow/skills/
├── public/                    ← 内置技能
│   ├── research/SKILL.md
│   └── ...
└── custom/                    ← 您的技能（在此添加）
    └── your-skill/SKILL.md
```

### SKILL.md结构

```markdown
---
name: my-skill
description: "技能描述"
license: MIT
allowed-tools:
  - web_search
  - write_file
---

# 智能体指令

逐步过程...
```

### 渐进式加载

技能仅在**需要时才加载**。这保持上下文窗口精简，适用于对token敏感的模型。

## 工具

### 工具类型

1. **内置** — DeerFlow自带（bash、ls、read_file、write_file等）
2. **社区** — 来自社区（tavily、jina_ai、firecrawl等）
3. **MCP** — 通过MCP标准连接
4. **自定义** — 您自己的Python函数

### 在config.yaml中配置工具

```yaml
tools:
  - name: web_search
    group: web
    use: src.community.tavily.tools:web_search_tool

tool_groups:
  - name: web
  - name: file:read
  - name: file:write
  - name: bash
```

## MCP服务器

**MCP**（Model Context Protocol）是连接外部工具的标准协议。连接类型：`stdio`（运行程序）、`sse`（通过SSE的URL）、`http`（通过HTTP的URL）。

## 通过API管理技能

- `GET /api/skills` — 列出所有技能
- `PUT /api/skills/{name}` — 启用/禁用
- `POST /api/skills/install` — 从.skill归档安装

## 总结

- 技能是扩展智能体能力的Markdown指令
- 工具是智能体调用来执行操作的函数
- 技能渐进式加载以节省上下文
- MCP允许连接外部工具
- 您可以创建自己的技能和工具
