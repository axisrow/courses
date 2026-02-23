---
title: "AI调试"
weight: 9
bookToc: true
---

# AI 调试

## AI 辅助调试

找 bug 是编程最难的部分之一。Windsurf 提供多种帮助方式。

## 方法一：问 Cascade

复制错误信息粘贴到 Cascade：

```
报错："TypeError: Cannot read property 'map' of undefined"
在 UserList.jsx 第 15 行
```

Cascade 会：
1. 查看文件
2. 解释错误原因
3. 建议修复方案

## 方法二：内联错误提示

看到红色下划线时：
1. 悬停查看错误
2. 点击 **Quick Fix**（或 `Ctrl+.`）
3. Windsurf 提供 AI 修复建议

## 方法三：终端调试

让 Cascade：
```
运行测试并解释为什么失败
```

Cascade 可以执行命令并分析输出。

## 常见调试场景

### Null/Undefined 错误
问："为什么 `user.name` 在这里可能是 undefined？"

### 逻辑错误
选中函数："这个函数对负数返回错误结果。能找到 bug 吗？"

### 性能问题
问："为什么这个函数很慢？如何优化？"

### API 错误
分享错误响应："这个 API 调用返回 403，这是我的代码..."

## 调试技巧

1. **分享完整错误** — 包括堆栈跟踪
2. **描述预期与实际行为**
3. **说明已经尝试过什么**
4. **使用断点** — Windsurf 支持标准 VS Code 调试

## 练习

找到代码中的 bug（或故意引入一个）。让 Cascade 帮你找到并修复。
