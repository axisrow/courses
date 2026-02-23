---
title: "理解代理"
weight: 5
bookToc: true
---

# 理解代理

## 什么是代理？

代理是分配到特定任务的 AI 助手。每个代理有：

- **ID** — 唯一名称（如 `code-reviewer`）
- **显示名称** — 友好名称（如"高级代码审查员"）
- **提示词** — 详细指令
- **引擎** — 使用的 AI 系统（Claude、Codex 等）

## 代理类型

### 1. 主代理（Main Agents）
主要执行者，工作流的每个步骤使用一个主代理。

```javascript
{
  id: 'code-reviewer',
  name: 'Code Reviewer',
  description: '审查代码质量',
  promptPath: 'prompts/review.md',
}
```

### 2. 子代理（Sub-Agents）
与主代理并行工作的助手。

```javascript
{
  id: 'frontend-dev',
  name: 'Frontend Developer',
  description: '负责 UI 组件',
  mirrorPath: 'prompts/frontend-mirror.md',
}
```

### 3. 控制器（Controller）
监督整个工作流并做决策的特殊代理。

## 选择引擎

| 引擎 | 最适合 |
|------|--------|
| Claude | 分析、审查、文档 |
| Codex | 代码生成、实现 |
| Cursor | IDE 集成任务 |

可以混合使用：

```javascript
resolveStep('planning', { engine: 'claude' }),
resolveStep('coding', { engine: 'codex' }),
resolveStep('review', { engine: 'claude' }),
```

## 总结

- 代理是工作流中的 AI 工作者
- 主代理、子代理和控制器各有角色
- 每个代理有 ID、名称、提示词和引擎
- 可以在一个工作流中混合不同引擎

> **恭喜！** 你完成了第一级。在第二级中，我们将开始构建真正的工作流。
