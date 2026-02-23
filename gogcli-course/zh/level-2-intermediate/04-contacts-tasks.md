---
title: "通讯录和任务"
weight: 9
bookToc: true
---

# 通讯录和任务

## 通讯录

### 搜索和查看

```bash
gog contacts search "小明" --max 10
gog contacts list --max 50
gog contacts get people/RESOURCE_NAME
```

### 创建联系人

```bash
gog contacts create --name "张三" --email zhang@example.com --phone "+8613800138000"
```

### 修改和删除

```bash
gog contacts update RESOURCE_NAME --phone "+8613900139000"
gog contacts delete RESOURCE_NAME
```

### 导出

```bash
gog contacts list --format csv > contacts.csv
```

## 任务

### 查看任务列表

```bash
gog tasks lists
gog tasks list                    # 默认列表
gog tasks list --list "工作"
```

### 创建任务

```bash
gog tasks add "完成报告" --due 2025-03-15
gog tasks add "买菜" --list "个人" --notes "番茄、鸡蛋、牛奶"
```

### 完成和删除

```bash
gog tasks done TASK_ID
gog tasks delete TASK_ID
```

## 练习

1. 添加一个新联系人
2. 创建一个带截止日期的任务
3. 导出通讯录为 CSV
