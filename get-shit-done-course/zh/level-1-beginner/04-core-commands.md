---
title: "GSD 核心命令"
level: 1
lesson: 4
language: zh
tags: [gsd, 命令, 工作流]
---

# GSD 核心命令

## 介绍

GSD 通过 Claude Code（或类似运行时）中的斜杠命令工作。主要循环：讨论 → 规划 → 执行 → 验证。

## 操作指南

### 主要循环

| 命令 | 功能 |
|------|------|
| `/gsd:new-project` | 从零创建项目 |
| `/gsd:discuss-phase N` | 规划前讨论阶段细节 |
| `/gsd:plan-phase N` | 研究并创建计划 |
| `/gsd:execute-phase N` | 并行波次执行计划 |
| `/gsd:verify-work N` | 手动验证结果 |

### 导航

| 命令 | 功能 |
|------|------|
| `/gsd:progress` | 显示当前状态 |
| `/gsd:help` | 列出所有命令 |

### 快速任务

```
/gsd:quick
> 在设置中添加暗色模式切换
```

不需要完整规划的任务。

### 阶段管理

| 命令 | 功能 |
|------|------|
| `/gsd:add-phase` | 添加阶段 |
| `/gsd:insert-phase N` | 插入紧急阶段 |
| `/gsd:remove-phase N` | 删除阶段 |

### 会话

| 命令 | 功能 |
|------|------|
| `/gsd:pause-work` | 保存进度 |
| `/gsd:resume-work` | 恢复进度 |

## 示例

```
/gsd:discuss-phase 1
/gsd:plan-phase 1
/gsd:execute-phase 1
/gsd:verify-work 1

/gsd:discuss-phase 2
...

/gsd:complete-milestone
```

## 总结

- 主要循环：discuss → plan → execute → verify
- `/gsd:quick` 用于小任务
- `/gsd:progress` 查看当前位置
- `/gsd:pause-work` 和 `/gsd:resume-work` 管理会话
