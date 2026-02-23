---
title: "数据转换"
weight: 7
bookToc: true
---

# 数据转换

## 为什么要转换数据？

不同服务的数据格式往往不一致。你需要重命名字段、过滤、合并和计算新值。

## 表达式

`{{ }}` 语法：

- `{{ $json.name }}` — 访问字段
- `{{ $json.price * 1.2 }}` — 计算
- `{{ $json.name.toUpperCase() }}` — 文本转换
- `{{ $json.date.split('T')[0] }}` — 提取部分字符串

### 特殊变量
- `$json` — 当前项的数据
- `$input` — 所有输入数据
- `$node["NodeName"].json` — 特定节点的数据
- `$now` — 当前日期时间

## 关键转换节点

### Set
重命名、添加、删除字段。**Keep Only Set** 只保留设定的字段。

### Code
JavaScript 或 Python 处理复杂转换：

```javascript
return items.map(item => {
  item.json.fullName = item.json.firstName + ' ' + item.json.lastName;
  item.json.isAdult = item.json.age >= 18;
  return item;
});
```

### Split Out
数组 → 独立项目。输入：1 项含 `tags: ["a", "b", "c"]`。输出：3 项。

### Aggregate
多个项目 → 一个含数组的项目。

### Sort / Limit / Remove Duplicates
排序、限制数量、去重。

## 常见模式

### 重命名字段
```
Set → "email" = {{ $json.contact_email }} → Keep Only Set: ON
```

### 过滤
```
IF → {{ $json.status }} equals "active" → 仅活跃项通过
```

### 合并数据源
```
Merge → Combine 模式 → 按共同字段匹配
```

## 练习

1. 获取用户列表：`https://jsonplaceholder.typicode.com/users`
2. 提取 `name`、`email` 和 `city`（来自 `address.city`）
3. 按姓名排序
4. 只保留前 5 个

## 小结

你已掌握数据转换。下一课学习错误处理。
