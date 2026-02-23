---
title: "高级模式"
level: 3
lesson: 2
language: zh
tags: [gsd, 模式, 高级]
---

# 高级模式

## 介绍

掌握基础后，你可以使用 GSD 的高级模式来处理复杂项目。

## 操作指南

### 棕地项目

对于现有代码库：

```
/gsd:map-codebase
```

启动并行代理分析技术栈、架构、代码规范和潜在问题。映射后，`/gsd:new-project` 会考虑现有代码。

### 插入紧急阶段

```
/gsd:insert-phase 3
```

在现有阶段之间插入，重新编号其余阶段。适用于热修复。

### 里程碑管理

```
/gsd:complete-milestone   # 完成、归档、标记
/gsd:new-milestone        # 开始新周期
/gsd:audit-milestone      # 验证目标达成
```

### 调试模式

```
/gsd:debug "重复登录时认证中断"
```

带持久状态的系统化调试。

### 带完整验证的快速模式

```
/gsd:quick --full
```

快速任务，但包含计划检查和验证。

### 跳过步骤

```
/gsd:plan-phase 1 --skip-research
/gsd:plan-phase 1 --skip-verify
```

## 示例

成熟项目的典型工作流：
```
/gsd:map-codebase
/gsd:new-milestone "v2.0"
/gsd:discuss-phase 1
/gsd:plan-phase 1
/gsd:execute-phase 1
/gsd:verify-work 1
/gsd:insert-phase 2          # 紧急修复
/gsd:plan-phase 2
```

## 总结

- `/gsd:map-codebase` 用于现有项目
- 通过 `insert-phase` 插入紧急阶段
- 里程碑用于版本管理
- 调试模式用于系统化调试
- Quick --full 用于带验证的快速任务
