---
title: "SKILL.md结构"
weight: 3
bookToc: true
---

# SKILL.md结构

## 简介

SKILL.md是每个技能的主文件。Codex通过阅读它来了解该做什么以及如何做。

## 整体结构

SKILL.md由两部分组成：

1. **YAML frontmatter** — 元数据（名称和描述）
2. **正文** — Markdown格式的指令

## YAML Frontmatter

位于文件开头的`---`之间：

```yaml
---
name: my-skill
description: 技能描述——何时以及为什么使用它。这是最重要的部分，因为Codex根据它来决定是否激活技能。
---
```

### `name`字段

- 技能名称
- 使用小写字母、数字和连字符
- 示例：`pdf`、`gh-fix-ci`

### `description`字段

- 技能最重要的部分！
- 描述技能**做什么**以及**何时使用**
- Codex在每个请求中都会读取它
- 要详尽：列出所有使用场景

## 正文

frontmatter之后是Markdown指令：

```markdown
# 技能名称

## 概述
技能功能的简要描述。

## 使用方法
分步指令。
```

### 正文的关键规则：

- **简洁** — 上下文窗口有限
- **不要重复** — 不要重复description中的"何时使用"
- **祈使语气** — 写"运行"、"检查"，而不是"技能会做"
- **不超过500行** — 超过则移至`references/`

## 总结

- SKILL.md由frontmatter（name + description）和正文（指令）组成
- description是最重要的部分，决定技能何时激活
- 正文应简洁实用
- 使用祈使语气
