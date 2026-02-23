---
title: "日历进阶"
weight: 7
bookToc: true
---

# 日历进阶

## 多个日历

```bash
gog calendar list-calendars
gog calendar list --calendar "工作"
gog calendar list --calendar "个人"
```

## 高级日程创建

```bash
gog calendar add "周会" \
  --date 2025-03-01 --time 10:00 --duration 30m \
  --calendar "工作" \
  --location "会议室A" \
  --description "每周团队同步"

# 重复日程
gog calendar add "站会" \
  --date 2025-03-01 --time 09:00 --duration 15m \
  --recurrence "FREQ=WEEKLY;BYDAY=MO,WE,FR"
```

## 邀请参与者

```bash
gog calendar add "评审会" \
  --date 2025-03-05 --time 14:00 \
  --attendee alice@company.com \
  --attendee bob@company.com
```

## 修改和删除

```bash
gog calendar update EVENT_ID --time 15:00
gog calendar delete EVENT_ID
gog calendar delete EVENT_ID --notify   # 通知参与者
```

## 查看空闲时间

```bash
gog calendar freebusy --date 2025-03-01 --days 5
gog calendar freebusy --email colleague@company.com
```

## 练习

1. 创建一个带参与者的重复日程
2. 查看下周的空闲时间
3. 修改一个已有日程的时间
