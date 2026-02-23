---
title: "条件逻辑"
weight: 9
bookToc: true
---

# 条件逻辑

## 工作流分支

不是所有数据都应走同一条路径。条件逻辑根据规则分流数据。

## IF 节点

两个输出：**True** 和 **False**。

### 条件类型
- **字符串**：等于、包含、开头、结尾、正则
- **数字**：等于、大于、小于、区间
- **布尔**：true、false

### 示例
```
条件：{{ $json.amount }} > 100
True  → 提交主管审批
False → 自动批准
```

### 组合条件
- **AND** — 所有条件都满足
- **OR** — 至少一个满足

## Switch 节点

多个输出，根据值路由。

```
字段：{{ $json.priority }}
输出 0: "low"    → 记录到表格
输出 1: "medium" → 发邮件
输出 2: "high"   → Slack 提醒 + 邮件
Fallback:        → 忽略
```

## Merge 节点

分支后重新合并数据。

### 模式
- **Append** — 合并所有项
- **Combine** — 按位置或字段匹配
- **Choose Branch** — 只传递一个分支

## Filter 节点

只保留匹配条件的项目，不匹配的被丢弃。

```
过滤：{{ $json.status }} equals "active"
```

## 循环

### Split In Batches
分批处理大数据集：
1. 设置批次大小（如 10）
2. 处理每批
3. 循环回 Split In Batches

## 实际示例：邮件路由

```
Email Trigger
  → IF（VIP 发件人？）
    → True：Slack 提醒
    → False：
      → Switch（主题包含？）
        → "发票" → 财务文件夹
        → "支持" → 创建工单
        → Fallback → 归档
```

## 练习

1. Manual Trigger 带 5 条数据（姓名、年龄、国家）
2. Filter：年龄 > 20
3. Switch：按国家路由
4. Merge：合并结果

## 小结

你已掌握分支逻辑。下一课学习数据库操作。
