---
title: "配置"
weight: 3
bookToc: true
---

# 配置

## 简介

Pi 提供通过配置文件、环境变量和命令进行灵活配置。

## 环境变量

主要 API 密钥变量：

```bash
export ANTHROPIC_API_KEY=sk-ant-...
export OPENAI_API_KEY=sk-...
export GOOGLE_API_KEY=...
export MISTRAL_API_KEY=...
export GROQ_API_KEY=...
```

## Pi 设置

在交互模式中，使用 `/settings`：

```
/settings
```

可以配置：
- 默认模型
- 思考级别
- 主题
- 自动完成行为

## 模型选择

```bash
pi --provider anthropic --model claude-sonnet-4-20250514
```

或交互式：

```
/model anthropic claude-sonnet-4-20250514
```

## 项目上下文文件

| 文件 | 用途 |
|------|------|
| `AGENTS.md` | 关于项目的代理指令 |
| `TOOLS.md` | 工具和环境说明 |
| `.pi/skills/` | 技能——上下文相关的指令 |

## 主题

Pi 支持终端 UI 的自定义主题。主题定义颜色和组件样式。

## 总结

- API 密钥通过环境变量设置
- 设置可通过 /settings 和 CLI 标志访问
- 上下文文件自定义代理行为
