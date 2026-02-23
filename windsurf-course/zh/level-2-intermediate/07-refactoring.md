---
title: "AI重构"
weight: 7
bookToc: true
---

# AI 重构

## 什么是重构？

重构是在不改变功能的情况下改进代码。Windsurf 让这变得简单。

## 快速重构

1. 选中要重构的代码
2. 右键 → **Windsurf: Refactor**
3. 或按 `Ctrl+Shift+R`

## 常见重构任务

### 重命名变量
选中变量，要求："重命名为更具描述性的名称"

### 提取函数
选中代码块："将这部分提取为单独的函数"

### 简化逻辑
选中复杂代码："简化这段逻辑"

### 转换模式
- "将回调转换为 async/await"
- "将类组件转换为函数组件"
- "用 map/filter 替换 for 循环"

## 用 Cascade 重构

```
重构 UserService 类：
- 拆分为更小的方法
- 添加错误处理
- 使用依赖注入
```

## 示例：重构前后

**重构前：**
```python
def process(d):
    r = []
    for i in d:
        if i['a'] > 10 and i['b'] == True:
            r.append(i['c'] * 2)
    return r
```

**重构后（AI）：**
```python
def process_active_items(items):
    return [
        item['value'] * 2
        for item in items
        if item['score'] > 10 and item['is_active']
    ]
```

## 小贴士

- 每次重构小部分
- 重构后运行测试
- 大改动前用 Git 提交——方便回退

## 练习

找到一个变量命名不好的函数，用 Windsurf 逐步重构。
