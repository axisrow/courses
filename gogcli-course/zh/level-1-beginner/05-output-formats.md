---
title: "输出格式"
weight: 5
bookToc: true
---

# 输出格式

gogcli 支持多种输出格式，方便不同场景使用。

## 可用格式

```bash
gog mail list --format table    # 表格（默认）
gog mail list --format json     # JSON
gog mail list --format csv      # CSV
gog mail list --format text     # 纯文本
```

## JSON 输出与 jq

```bash
gog mail list --format json | jq '.[0].subject'
gog calendar list --format json | jq 'length'
```

## CSV 导出

```bash
gog mail list --format csv > emails.csv
gog contacts list --format csv > contacts.csv
```

## 设置默认格式

```bash
gog config set default_format json
```

## 管道操作

```bash
gog mail list --format text | grep "重要"
gog drive list --format csv | head -20
```

## 练习

1. 用不同格式列出邮件，比较输出
2. 用 JSON 格式输出并用 jq 提取字段
3. 导出通讯录为 CSV 文件
