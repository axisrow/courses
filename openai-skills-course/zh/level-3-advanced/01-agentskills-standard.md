---
title: "AgentSkills标准（agentskills.io）"
weight: 1
bookToc: true
---

# AgentSkills标准（agentskills.io）

## 简介

AgentSkills是描述AI代理技能的开放标准。发布于[agentskills.io](https://agentskills.io)，它定义了不同AI代理都可以使用的统一格式——不仅限于Codex。

## 为什么需要标准？

没有标准，每个AI代理使用自己的技能格式，导致技能不可移植。AgentSkills解决了这个问题：**编写一次，到处使用**。

## 核心原则

### 1. 文件夹即技能
技能是一个普通文件夹。不是包，不是容器——只是文件夹。

### 2. SKILL.md作为入口点
每个技能必须在根目录有一个`SKILL.md`。这是唯一必需的文件。

### 3. YAML Frontmatter

```yaml
---
name: skill-name
description: 技能描述
---
```

### 4. agents/文件夹
每个代理可以有自己的配置文件：

```
agents/
├── openai.yaml
├── anthropic.yaml
└── other.yaml
```

### 5. 资源
标准资源文件夹：
- `scripts/` — 可执行脚本
- `references/` — 参考文档
- `assets/` — 输出文件

## 了解更多

- 标准网站：[agentskills.io](https://agentskills.io)
- 文档：[developers.openai.com/codex/skills](https://developers.openai.com/codex/skills)
- 仓库：[github.com/openai/skills](https://github.com/openai/skills)

## 总结

- AgentSkills是AI代理技能的开放标准
- 基于包含SKILL.md的文件夹
- 确保跨代理的可移植性
- 简单格式：YAML frontmatter + Markdown指令
