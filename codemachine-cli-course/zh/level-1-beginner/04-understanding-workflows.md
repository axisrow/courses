---
title: "理解工作流"
weight: 4
bookToc: true
---

# 理解工作流

## 什么是工作流？

工作流是告诉 AI 代理做什么、按什么顺序做的步骤序列。每个步骤包含：

- **代理** — 哪个 AI 执行任务
- **提示词** — 告诉代理做什么的指令
- **设置** — 代理的行为方式

## 现实例子

假设你要为网站开发新功能：

1. 研究需求
2. 规划架构
3. 编写代码
4. 审查代码
5. 编写测试

在 CodeMachine 中，每个步骤都有专属的代理和指令。

## 工作流文件

```javascript
export default {
  name: 'Feature Builder',
  steps: [
    resolveStep('research-agent'),
    resolveStep('planning-agent'),
    resolveStep('coding-agent'),
    resolveStep('review-agent'),
    resolveStep('testing-agent'),
  ],
};
```

## 三种构建块

| 构建块 | 用途 | 示例 |
|--------|------|------|
| **Step（步骤）** | 单个任务 | "审查代码" |
| **Module（模块）** | 可循环的任务 | "检查并修复" |
| **Folder（文件夹）** | 一组相关步骤 | "所有设置步骤" |

## 步骤如何连接

步骤按顺序执行：

```
步骤 1 → 步骤 2 → 步骤 3 → 步骤 4 → 完成！
```

## 总结

- 工作流是保存的 AI 任务序列
- 每个步骤有代理、提示词和设置
- 步骤、模块和文件夹是构建块

> **下一课：** 理解代理。
