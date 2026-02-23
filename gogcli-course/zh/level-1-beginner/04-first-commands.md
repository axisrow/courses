---
title: "第一批命令"
weight: 4
bookToc: true
---

# 第一批命令

## 查看邮件

```bash
gog mail list
gog mail list --max 5
gog mail read MESSAGE_ID
```

## 发送邮件

```bash
gog mail send --to friend@gmail.com --subject "你好" --body "这是测试邮件"
```

## 查看日历

```bash
gog calendar list
gog calendar list --date 2025-01-15
gog calendar list --days 7
```

## 创建日程

```bash
gog calendar add "团队会议" --date 2025-01-20 --time 14:00 --duration 1h
```

## 查看云端硬盘

```bash
gog drive list
gog drive list --folder "我的文档"
```

## 获取帮助

每个命令都有帮助：

```bash
gog mail --help
gog calendar add --help
```

## 练习

1. 列出最近 5 封邮件
2. 给自己发一封测试邮件
3. 查看今天的日历日程
