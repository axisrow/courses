---
title: "基础AI自动补全"
weight: 5
bookToc: true
---

# 基础 AI 自动补全

## 工作原理

Windsurf 用 AI 预测你想输入的内容。建议以灰色文字出现，称为 **ghost text**。

## 接受建议

- **Tab** — 接受完整建议
- **Ctrl+→** — 逐词接受
- **Escape** — 取消建议

## 补全类型

### 1. 单行补全
输入一行时，Windsurf 补全它：

```javascript
const greeting = "你好, " // AI 建议: + name + "!"
```

### 2. 多行补全
在函数签名或注释后，AI 编写函数体：

```python
def fibonacci(n):
    # AI 编写整个函数体
```

### 3. 注释驱动
写一个注释，AI 将其转换为代码：

```javascript
// 从 API 获取用户数据并返回姓名
```

## 获得更好建议的技巧

1. **清晰的变量名** — `userEmail` 比 `x` 效果好
2. **添加注释** — 引导 AI
3. **提供上下文** — import 语句帮助 AI 理解项目
4. **具体描述** — "按日期降序排列对象数组" 比 "排序" 好

## 支持的语言

支持 70+ 种语言：Python、JavaScript、TypeScript、Java、C++、Go、Rust、PHP、Ruby、Swift 等。

## 设置

在 Settings 中可以：
- 开启/关闭自动补全
- 更改建议延迟
- 按文件类型过滤

## 练习

1. 用任何语言打开新文件
2. 写 3 个描述函数的注释
3. 让 Windsurf 生成每个函数
4. 检查并编辑结果
