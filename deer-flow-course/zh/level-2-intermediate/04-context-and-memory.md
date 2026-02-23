---
title: "上下文与记忆"
weight: 4
bookToc: true
---

# 上下文与记忆

## 简介

大多数聊天机器人在关闭窗口后会忘记一切。DeerFlow不会。它有两种机制：**上下文管理**（会话内）和**长期记忆**（跨会话）。

## 上下文（会话内）

### 上下文窗口问题

每个AI模型都有文本限制——**上下文窗口**（例如128,000个token ≈ 96,000个单词）。如果对话太长，旧消息会"溢出"。

### DeerFlow如何解决这个问题

1. **隔离的子智能体上下文** — 每个子智能体在自己的上下文中工作，节省空间
2. **摘要** — 当上下文接近限制时，自动压缩旧消息
3. **卸载到文件系统** — 中间结果保存为文件而非保留在上下文中

```yaml
summarization:
  enabled: true
  trigger:
    type: tokens
    threshold: 100000
  keep:
    recent_messages: 10
```

## 长期记忆（跨会话）

### 记忆如何工作

DeerFlow**自动提取**对话中的重要信息并保存。下次，这些信息会被包含在系统提示中。

### 记住什么

存储在`memory.json`中：

- **用户上下文**：工作背景、个人信息
- **历史**：近期和长期背景
- **事实**：具有内容、类别和置信度的离散项目

### 事实类别

| 类别 | 示例 |
|------|------|
| `preference` | "喜欢简洁的回答" |
| `knowledge` | "了解Python和JavaScript" |
| `context` | "在初创公司工作" |
| `behavior` | "经常要求代码示例" |
| `goal` | "想学Go语言" |

### 记忆配置

```yaml
memory:
  enabled: true
  injection_enabled: true
  storage_path: .deer-flow/memory.json
  debounce_seconds: 30
  max_facts: 100
  fact_confidence_threshold: 0.7
  max_injection_tokens: 2000
```

### 记忆API

- `GET /api/memory` — 查看当前记忆
- `POST /api/memory/reload` — 强制重载
- `GET /api/memory/status` — 系统状态

## 总结

- 上下文通过子智能体隔离和摘要来管理
- 长期记忆保存事实、偏好和上下文
- 记忆在后台自动更新
- 本地存储在`memory.json`中，由您控制
- 可通过`config.yaml`配置，通过API管理
