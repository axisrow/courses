---
title: "文档技能（DOCX、PDF、PPTX、XLSX）"
weight: 3
bookToc: true
---

# 文档技能

## 简介

Anthropic为主要文档格式创建了技能，支持Claude的文件创建功能。

## DOCX — Word文档

创建、编辑、添加评论、跟踪更改。

```
docx/
├── SKILL.md
├── scripts/（comment.py, accept_changes.py, office/）
└── LICENSE.txt
```

## PDF、PPTX、XLSX

类似结构，分别用于PDF文档、PowerPoint演示文稿和Excel电子表格。

## 特点

1. 包含处理二进制格式的**脚本**
2. 包含验证用的**XML模式**
3. **源码可见** — 可查看但非开源

## 总结

- Anthropic提供DOCX、PDF、PPTX、XLSX技能
- 文档技能使用脚本处理文件
- 可作为复杂技能的学习范例
