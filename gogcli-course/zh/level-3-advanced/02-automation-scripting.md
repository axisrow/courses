---
title: "自动化与脚本"
weight: 12
bookToc: true
---

# 自动化与脚本

## 基础脚本

用 `--format json` 输出便于程序处理。

### 示例：每日汇报

```bash
#!/bin/bash
TODAY=$(date +%Y-%m-%d)
EVENTS=$(gog calendar list --date "$TODAY" --format text)
UNREAD=$(gog mail list --unread --max 5 --format text)

gog mail send \
  --to boss@company.com \
  --subject "每日汇报 $TODAY" \
  --body "日程:\n$EVENTS\n\n未读邮件:\n$UNREAD"
```

## 配合 jq 使用

```bash
gog mail list --unread --format json | jq -r '.[].id'
gog drive list --format json | jq 'length'
```

## 批量处理

```bash
for id in $(gog drive list --folder "报告" --format json | jq -r '.[].id'); do
  gog drive download "$id" -o ./reports/
done
```

## 定时任务 (Cron)

```bash
# 每天早上 9 点发送汇报
0 9 * * * /home/user/scripts/daily-report.sh
```

## 练习

1. 写一个脚本归档 30 天前的已读邮件
2. 设置定时任务每周备份云端硬盘文件
