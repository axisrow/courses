---
title: "安装技能"
weight: 5
bookToc: true
---

# 安装技能

## 简介

从Anthropic仓库和自定义技能的安装步骤。

## 从Anthropic仓库安装

```bash
git clone https://github.com/anthropics/skills.git

# 在Claude Code中
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
```

## 自定义技能

1. 创建技能文件夹：`mkdir my-skill`
2. 创建`SKILL.md`文件
3. 连接到Claude（Code/web/API）

## 总结

- 通过Claude Code（`/plugin`）或手动安装技能
- Anthropic仓库包含现成的技能集
- 自定义技能只需包含`SKILL.md`的文件夹
