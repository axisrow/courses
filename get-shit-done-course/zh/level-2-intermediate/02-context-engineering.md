---
title: "上下文工程"
level: 2
lesson: 2
language: zh
tags: [gsd, 上下文工程, 文件]
---

# 上下文工程

## 介绍

上下文工程是给 AI 提供恰到好处的上下文的艺术。不多不少。GSD 自动完成这项工作。

## 操作指南

### GSD 中的上下文层次

| 文件 | 角色 | 何时加载 |
|------|------|---------|
| `PROJECT.md` | 项目愿景 | 始终 |
| `STATE.md` | 当前状态、决策 | 始终 |
| `ROADMAP.md` | 进度 | 规划时 |
| `REQUIREMENTS.md` | 需求 | 规划时 |
| `CONTEXT.md` | 阶段决策 | 阶段规划时 |
| `RESEARCH.md` | 研究发现 | 规划时 |
| `PLAN.md` | 具体任务 | 执行时 |

### 大小限制

GSD 控制文件大小——不是为了方便，而是因为 Claude 在大上下文中质量会下降。每个文件都经过大小优化。

### "按需知道"原则

执行者不会看到所有研究和所有计划。它只看到：
- PROJECT.md — 项目理解
- 它的具体 PLAN.md — 要做什么
- STATE.md — 当前决策

这给它干净的 200k tokens 用于工作。

## 示例

糟糕的上下文：
```
"记得吗，30 条消息前我们决定用 PostgreSQL？"
```

好的上下文（GSD）：
```
STATE.md: database=PostgreSQL, orm=Prisma, deployed=Vercel
```

## 总结

- 上下文工程 = 在正确的时间提供正确的上下文
- 每个代理只接收它需要的文件
- 文件大小受控以获得最佳质量
- 状态存储在文件中，而非对话记忆
