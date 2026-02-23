---
title: "项目配置"
level: 2
lesson: 4
language: zh
tags: [gsd, 配置, 设置]
---

# 项目配置

## 介绍

GSD 可以灵活配置。你可以控制工作模式、模型配置文件、git 策略和工作流代理。

## 操作指南

### 配置

设置存储在 `.planning/config.json`。通过 `/gsd:settings` 更改。

### 工作模式

| 设置 | 选项 | 默认值 |
|------|------|--------|
| `mode` | `yolo`, `interactive` | `interactive` |
| `depth` | `quick`, `standard`, `comprehensive` | `standard` |

- **yolo** — 每步自动批准
- **interactive** — 需要你的确认
- **quick/standard/comprehensive** — 规划深度

### 模型配置文件

```
/gsd:set-profile budget
```

| 配置文件 | 规划 | 执行 | 验证 |
|---------|------|------|------|
| `quality` | Opus | Opus | Sonnet |
| `balanced` | Opus | Sonnet | Sonnet |
| `budget` | Sonnet | Sonnet | Haiku |

### 工作流代理

| 代理 | 默认 | 功能 |
|------|------|------|
| `research` | 开启 | 规划前研究领域 |
| `plan_check` | 开启 | 执行前验证计划 |
| `verifier` | 开启 | 执行后确认结果 |
| `auto_advance` | 关闭 | 自动链接 discuss→plan→execute |

### Git 策略

| 策略 | 功能 |
|------|------|
| `none` | 提交到当前分支 |
| `phase` | 每个阶段一个分支 |
| `milestone` | 每个里程碑一个分支 |

## 示例

```
/gsd:settings
> 设置 mode=yolo, depth=comprehensive, profile=quality
```

## 总结

- 配置在 `.planning/config.json`
- 三个模型配置文件：quality、balanced、budget
- 模式：yolo（自动）和 interactive（手动）
- Git 策略：none、phase、milestone
- 代理可以开关以节省 tokens
