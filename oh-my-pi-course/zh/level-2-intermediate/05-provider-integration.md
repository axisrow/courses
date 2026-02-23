---
title: "服务商集成"
level: 2
lesson: 5
lang: zh
tags: [服务商, 模型, 角色, 多凭证]
---

# 服务商集成

## 介绍

OMP 支持数十个 AI 服务商，允许灵活管理模型。

## 模型角色

```
/model
```

| 角色 | 用途 |
|------|------|
| default | 常规工作 |
| smol | 快速/低成本任务 |
| slow | 深度分析 |
| plan | 规划 (/plan) |
| commit | 提交和 changelog |

CLI 切换：

```bash
omp --model anthropic/claude-sonnet-4
omp --smol anthropic/claude-haiku
omp --slow anthropic/claude-opus
```

快捷键：`Ctrl+P` 循环模型，`Ctrl+L` 选择器。

## 多凭证支持

- API 密钥间轮询
- 速率限制时自动回退
- 一致性哈希确保稳定分配

## 支持的 API

`openai-completions`、`openai-responses`、`anthropic-messages`、`google-generative-ai`、`google-vertex`、`azure-openai-responses`、`openai-codex-responses`

## Cursor 服务商

使用 Cursor Pro 订阅：

```
/login
# 选择 Cursor
```

## Ollama（本地模型）

```yaml
# ~/.omp/agent/models.yml
providers:
  ollama:
    baseUrl: http://localhost:11434/v1
    api: openai-completions
    models:
      - id: llama-3.1-8b
        name: Llama 3.1 8B
        contextWindow: 128000
```

## MCP 和插件

```bash
omp plugin install <name>
omp plugin enable <name>
omp plugin doctor
```

## 总结

OMP 支持众多服务商，提供灵活的角色配置、多凭证和 MCP 集成。
