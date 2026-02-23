---
title: "Frontmatter和元数据"
weight: 2
bookToc: true
---

# Frontmatter和元数据

## 简介

Frontmatter是`SKILL.md`顶部的YAML块，定义技能元数据。其质量决定Claude何时以及如何激活技能。

## 必填字段

### name

```yaml
name: my-skill-name
```

规则：仅小写字母和连字符，唯一。

### description

最重要的字段：

```yaml
description: >
  创建MCP服务器的指南。当用户需要构建MCP服务器时使用。
```

好的描述包含：功能说明、使用时机、激活关键词。

## 示例

❌ 差：`description: Helps with code`

✅ 好：`description: Reviews Python code for security vulnerabilities and PEP 8 compliance. Use when user asks to review Python code.`

## 总结

- Frontmatter决定Claude何时激活技能
- `description`是正确激活的关键字段
- 在描述中包含触发词和关键词
