---
title: "配置"
level: 2
lesson: 3
lang: zh
tags: [配置, 设置, config.yml]
---

# 配置

## 介绍

OMP 通过全局和项目级别的配置文件进行配置。

## 全局配置

文件：`~/.omp/agent/config.yml`

```yaml
theme:
  dark: titanium
  light: light

modelRoles:
  default: anthropic/claude-sonnet-4-20250514

defaultThinkingLevel: medium

compaction:
  enabled: true
  reserveTokens: 16384
  keepRecentTokens: 20000
  autoContinue: true

skills:
  enabled: true

terminal:
  showImages: true
```

## CLI 管理

```bash
omp config list           # 所有设置
omp config get theme      # 获取值
omp config set theme.dark dracula  # 设置值
omp config reset theme    # 重置
omp config path           # 文件路径
```

## 项目上下文文件

OMP 从多个目录加载上下文：`.omp/`、`.claude/`、`.codex/`、`.gemini/`

`AGENTS.md`、`CLAUDE.md` 等文件提供项目指导。

## 自定义系统提示词

1. **项目级：** `.omp/SYSTEM.md`
2. **全局级：** `~/.omp/agent/SYSTEM.md`

```bash
omp --system-prompt "你是 Python 专家"
omp --append-system-prompt "始终编写测试"
```

## 自定义模型

文件 `~/.omp/agent/models.yml`：

```yaml
providers:
  ollama:
    baseUrl: http://localhost:11434/v1
    api: openai-completions
    models:
      - id: llama-3.1-8b
        name: Llama 3.1 8B
        contextWindow: 128000
        maxTokens: 32000
```

## 主题

65+ 内置主题。自定义：`~/.omp/agent/themes/*.json`。

## 总结

OMP 配置灵活 — 从全局设置到项目上下文和自定义模型。
