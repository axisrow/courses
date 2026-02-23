---
title: "什么是Agent Skills"
weight: 1
bookToc: true
---

# 什么是Agent Skills

## 简介

Agent Skills（代理技能）是包含指令、脚本和资源的文件夹，AI代理可以发现并使用它们来执行特定任务。原则很简单：**编写一次，到处使用**。

想象一下给新员工培训。您给他们指南："这是我们处理客户的方式"，"这是报告模板"。Skills的工作方式相同——它们"训练"AI代理Codex执行特定任务。

## 为什么需要技能？

没有技能，Codex是一个聪明但通用的助手。有了技能，它就变成了**专家**：

- 📸 **screenshot** — 截屏
- 📄 **pdf** — 处理PDF文档
- 🎨 **figma** — 将Figma设计转换为代码
- 🚀 **vercel-deploy** — 部署应用到Vercel

## 工作原理

每个技能都是一个普通的文件夹：

```
技能名称/
├── SKILL.md          — 主指令文件
├── agents/
│   └── openai.yaml   — UI元数据
├── scripts/          — 可执行脚本（可选）
├── references/       — 参考文档（可选）
└── assets/           — 资源文件（可选）
```

最重要的文件是 **SKILL.md**。Codex通过阅读它来了解该做什么。

## 技能的三个类别

| 类别 | 描述 | 安装方式 |
|------|------|----------|
| `.system` | 内置于Codex | 自动 |
| `.curated` | 经OpenAI验证 | 通过skill-installer |
| `.experimental` | 社区实验性 | 通过skill-installer |

## 总结

- Agent Skills为特定任务扩展Codex的能力
- 每个技能是一个包含指令和资源的文件夹
- 技能分为系统、精选和实验性三类
- 技能的主文件是SKILL.md
