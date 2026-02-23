---
title: "使用不同的代理"
level: 2
lesson: 5
language: zh
tags: [gsd, claude-code, opencode, gemini]
---

# 使用不同的代理

## 介绍

GSD 支持三个运行时：Claude Code、OpenCode 和 Gemini CLI。安装和命令相同——只有执行环境不同。

## 操作指南

### 支持的运行时

| 运行时 | 描述 | 标志 |
|--------|------|------|
| **Claude Code** | 主要，来自 Anthropic | `--claude` |
| **OpenCode** | 开源，免费模型 | `--opencode` |
| **Gemini CLI** | Google Gemini | `--gemini` |

### 为特定运行时安装

```bash
npx get-shit-done-cc --claude --global
npx get-shit-done-cc --opencode --global
npx get-shit-done-cc --gemini --global
npx get-shit-done-cc --all --global       # 全部三个
```

### 文件位置

| 运行时 | 全局路径 |
|--------|---------|
| Claude Code | `~/.claude/` |
| OpenCode | `~/.config/opencode/` |
| Gemini | `~/.gemini/` |

### 差异

核心 GSD 逻辑在所有运行时中相同。差异：
- **模型** — 每个运行时使用自己的模型
- **命令** — 斜杠命令语法可能略有不同
- **子代理** — 并行实现取决于运行时

## 示例

```bash
npx get-shit-done-cc --all --global

# 在 Claude Code 中验证
claude
/gsd:help

# 在 OpenCode 中验证
opencode
/gsd:help
```

## 总结

- GSD 在 Claude Code、OpenCode 和 Gemini CLI 中工作
- 一条安装命令加运行时标志
- 逻辑和命令相同
- 可以同时为所有运行时安装
