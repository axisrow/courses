---
title: "Cascade AI助手"
weight: 6
bookToc: true
---

# Cascade AI 助手

## 什么是 Cascade？

Cascade 是 Windsurf 内置的 AI 助手。与自动补全不同，Cascade 可以：

- 阅读和理解整个项目
- 同时修改多个文件
- 解释代码并提供改进建议
- 代替你执行终端命令

## 打开方式

- 点击活动栏中的 **Cascade 图标**
- 按 `Ctrl+Shift+L`（Windows/Linux）或 `Cmd+Shift+L`（Mac）

## 模式

### 编写模式
让 Cascade 编写或修改代码：

- "用 Express.js 创建 REST API"
- "给登录函数添加错误处理"
- "为 User 类编写单元测试"

### 聊天模式
提问而不修改代码：

- "解释这个函数的作用"
- "处理这个错误的最佳方式是什么？"
- "为什么这个测试失败了？"

## 高效使用

### 具体描述
❌ "修复 bug"
✅ "修复 `processOrder()` 第 45 行的空指针错误"

### 提供上下文
打开 Cascade 前选中代码，它会使用选中内容作为上下文。

### 审查更改
Cascade 在应用更改前显示 diff。务必审查后再接受。

## 示例流程

1. 打开 Cascade
2. 输入："添加一个验证邮箱和密码的登录端点"
3. 查看建议的更改
4. 对每个文件点击 **Accept** 或 **Reject**
5. 测试结果

## 限制

- 100 个文件以内的项目效果最好
- 非常大的文件可能减慢响应
- 复杂的架构更改可能需要多次提示

## 练习

打开一个项目，让 Cascade 添加新功能。仔细审查 diff。
