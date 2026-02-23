---
title: "高级工作流"
level: 3
lesson: 3
lang: zh
---

# 高级工作流

## 简介

复杂工作流：并行代理、代码审查、git worktrees。

## Git Worktrees

`using-git-worktrees` 技能创建隔离工作区：

```bash
git worktree add ../project-feature-x feature-x
```

优势：主分支不受影响，可并行开发，测试基线干净。

## 并行代理

`dispatching-parallel-agents`：
1. 识别独立任务
2. 为每个启动子代理
3. 收集结果
4. 验证兼容性

## 代码审查工作流

两阶段：
- **requesting-code-review** — 审查前清单
- **receiving-code-review** — 处理反馈，严重性分类

## 完成工作流

`finishing-a-development-branch`：验证测试 → 选择合并/PR/保留/丢弃 → 清理。

## 总结

- Git worktrees 提供隔离
- 并行代理加速工作
- 代码审查是必需步骤
- 工作流可灵活组合
