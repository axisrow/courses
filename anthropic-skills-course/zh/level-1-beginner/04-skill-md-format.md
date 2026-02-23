---
title: "SKILL.md格式"
weight: 4
bookToc: true
---

# SKILL.md格式

## 简介

`SKILL.md`是每个技能的主文件，包含元数据和Claude的指令。

## 文件结构

```markdown
---
name: my-skill-name
description: 技能描述及使用时机
---

# 技能名称

Claude将遵循的指令。

## 示例
- 示例1
- 示例2

## 准则
- 准则1
- 准则2
```

## Frontmatter（元数据）

文件顶部`---`之间的YAML块。必填字段：

| 字段 | 说明 |
|------|------|
| `name` | 唯一标识符（小写字母、连字符）|
| `description` | 技能的完整描述及使用时机 |

## 正文

Frontmatter之后是标准Markdown，包含指令、示例和准则。

## 总结

- `SKILL.md`是每个技能的必需文件
- Frontmatter包含`name`和`description`
- 正文是给Claude的Markdown指令
- 指令越具体，效果越好
