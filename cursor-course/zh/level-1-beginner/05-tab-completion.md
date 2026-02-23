---
title: "Tab 自动补全 — 你的 AI 助手"
weight: 5
bookToc: true
---

# Tab 自动补全 — 你的 AI 助手

## 什么是 Tab 自动补全？

当你输入代码时，Cursor 会预测你接下来想写什么。建议以**灰色文字**出现。按 `Tab` 接受。

这是在 Cursor 中使用 AI 最简单、最常用的方式。

## 工作原理

1. **你输入**几个字符或一行代码
2. **Cursor 建议**下一行、代码块或整个函数
3. **按 Tab** 接受，或继续输入忽略建议

AI 会考虑：
- 你已经写的内容
- 项目中的其他文件
- 使用的编程语言
- 常见编码模式

## 示例

### 示例 1：编写函数
你输入：
```python
def calculate_total(items):
```
Cursor 建议：
```python
    total = 0
    for item in items:
        total += item.price
    return total
```

### 示例 2：先写注释
你写了一条注释：
```javascript
// 检查邮箱是否有效的函数
```
Cursor 在注释下方建议完整函数。

### 示例 3：重复模式
如果你写了：
```python
user.first_name = data["first_name"]
user.last_name = data["last_name"]
```
Cursor 会自动预测下一个字段。

## 获得更好建议的技巧

1. **写清晰的注释** — AI 会阅读你的注释
2. **使用描述性名称** — `calculateTotalPrice` 比 `calc` 效果好
3. **保持相关文件打开** — Cursor 使用打开的文件作为上下文

## 部分接受建议

- **Tab** — 接受完整建议
- **Ctrl+→** / **Cmd+→** — 逐词接受
- **Escape** — 取消建议

## 小结

- AI 建议以灰色文字出现
- 按 `Tab` 接受
- 写清晰的注释以获得更好的结果
- 这只是开始——更强大的工具在后面！
