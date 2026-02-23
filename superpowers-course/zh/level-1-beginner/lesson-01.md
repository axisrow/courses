---
title: "什么是 Superpowers"
level: 1
lesson: 1
lang: zh
---

# 什么是 Superpowers

## 简介

Superpowers 简介——面向编码代理的技能框架。

Superpowers 是 Jesse Vincent（obra）开发的框架，它将普通的编码代理变成系统化的开发者。代理不会混乱地生成代码，而是遵循清晰的流程：先理解任务，再设计方案，最后编写代码。

## 什么是 Superpowers

Superpowers 是一套在编码代理中自动激活的**技能（skills）**。技能是在开发每个阶段指导代理的指令。

### 核心原则

- **测试驱动开发** — 先写测试
- **系统化** — 流程优于猜测
- **降低复杂性** — 以简洁为首要目标
- **证据优于声明** — 验证后再宣布成功

### 基本工作流

1. **头脑风暴** — 代理澄清任务，提出问题
2. **规格说明** — 将需求形式化为文档
3. **计划** — 将工作分解为 2-5 分钟的任务
4. **子代理** — 为每个任务启动独立代理
5. **代码审查** — 检查结果
6. **完成** — 合并或创建 PR

### 可用技能

| 类别 | 技能 |
|------|------|
| 测试 | test-driven-development |
| 调试 | systematic-debugging, verification-before-completion |
| 协作 | brainstorming, writing-plans, executing-plans, subagent-driven-development |
| Git | using-git-worktrees, finishing-a-development-branch |
| 元技能 | writing-skills, using-superpowers |

## 示例

你告诉代理：「构建一个笔记 REST API」。没有 Superpowers，代理会立即开始编码。有了 Superpowers：

1. 代理会问：「笔记有哪些字段？需要认证吗？用什么数据库？」
2. 分段展示规格说明
3. 创建 10-15 个任务的计划
4. 通过子代理用 TDD 执行每个任务

## 总结

- Superpowers 是编码代理的技能框架
- 技能自动激活
- 核心流程：规格说明 → 计划 → 子代理 → TDD
- 支持 Claude Code、Cursor、Codex、OpenCode
