---
title: "从零创建技能"
weight: 1
bookToc: true
---

# 从零创建技能

## 简介

创建技能很简单：需要一个包含`SKILL.md`文件的文件夹。

## 步骤1：定义任务

创建前回答：
- 技能应解决什么任务？
- Claude何时应激活它？
- 预期输出是什么？

## 步骤2：创建结构

```bash
mkdir code-reviewer && cd code-reviewer
```

## 步骤3：编写SKILL.md

```markdown
---
name: code-reviewer
description: Reviews Python code for best practices and security. Use when user asks to review Python code.
---

# 代码审查技能

## 审查流程
1. 阅读整个代码库
2. 检查安全问题
3. 检查性能问题
4. 验证PEP 8合规性

## 输出格式
- 🔴 严重 — 安全漏洞
- 🟡 警告 — 性能问题
- 🔵 信息 — 风格建议
```

## 步骤4：测试

连接技能并向Claude提出相关问题。

## 总结

- 技能是包含`SKILL.md`的文件夹
- 从定义任务和预期输出开始
- 编写具体的指令和示例
