---
title: "项目定制"
level: 2
lesson: 4
lang: zh
---

# 项目定制

## 简介

为特定项目和团队定制 Superpowers。

## AGENTS.md

项目根目录的 `AGENTS.md` 文件是主要的自定义方式：

```markdown
# AGENTS.md

## 技术栈
- TypeScript, Node.js 20
- PostgreSQL, Prisma ORM
- Jest 测试

## 约定
- 所有文件在 src/
- 测试与代码并列：src/foo.ts → src/foo.test.ts
- 使用 ESM

## 禁止
- 不使用 any 类型
- 不用 console.log 调试
```

## 适配已有项目

1. 确保测试通过（`npm test`）
2. 代理使用 git worktrees 隔离
3. 现有代码成为新任务的上下文

## 总结

- AGENTS.md 是主要配置文件
- 描述技术栈、约定和限制
- Superpowers 适应你的项目
