---
title: "Agent Skills — 开放标准"
weight: 1
bookToc: true
---

# Agent Skills — 开放标准

## 简介

Agent Skills是一个开放标准，定义AI代理如何使用技能。规范位于[agentskills.io](https://agentskills.io)。

## 为什么需要标准

没有标准，每个AI提供商都创建自己的技能格式。标准确保：

- **可移植性** — 技能跨AI系统工作
- **兼容性** — 不同作者的技能协同工作
- **生态系统** — 通用格式促进技能创建

## 规范定义

1. 文件格式 — 带YAML frontmatter的SKILL.md
2. 元数据 — 必填和可选字段
3. 文件夹结构 — 脚本和资源放置
4. 发现机制 — 代理如何找到和激活技能
5. 执行方式 — 代理如何遵循指令

## 总结

- Agent Skills是面向AI代理的开放标准
- 确保可移植性和兼容性
- 当前规范在agentskills.io
- Claude的Skills是该标准的一个实现
