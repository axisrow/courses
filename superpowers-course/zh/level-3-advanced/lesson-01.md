---
title: "Superpowers 架构"
level: 3
lesson: 1
lang: zh
---

# Superpowers 架构

## 简介

深入了解技能系统架构。

## 仓库结构

```
superpowers/
├── skills/
│   ├── brainstorming/SKILL.md
│   ├── test-driven-development/SKILL.md
│   └── ...
├── docs/
├── .claude/
├── .codex/
├── .opencode/
└── README.md
```

## 技能如何工作

每个技能是一个 `SKILL.md` 文件，包含代理指令。代理遇到特定上下文时加载相应技能。

### 技能链

```
brainstorming → using-git-worktrees → writing-plans → 
subagent-driven-development → test-driven-development → 
requesting-code-review → finishing-a-development-branch
```

## 技能间通信

通过工件通信：
- 规格说明（brainstorming → writing-plans）
- 计划（writing-plans → subagent-driven-development）
- 代码和测试（subagent-driven-development → code-review）

## 总结

- 技能在 `skills/*/SKILL.md` 中
- 根据上下文自动激活
- 形成从想法到合并的链条
- 通过工件通信
