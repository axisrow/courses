---
title: "跟踪与通知"
weight: 14
bookToc: true
---

# 跟踪与通知

## watch 命令

实时监控变化：

```bash
gog mail watch
gog mail watch --label INBOX
gog calendar watch
gog drive watch --folder "项目"
```

## 过滤

```bash
gog mail watch --from boss@company.com
gog mail watch --subject "紧急"
gog calendar watch --calendar "工作"
```

## 输出处理

```bash
gog mail watch --format json >> mail-log.jsonl
gog mail watch --format json | jq '.subject'
```

## Webhook

```bash
gog mail watch --webhook https://your-server.com/hook
gog drive watch --webhook https://your-server.com/drive-hook
```

## 结合自动化

```bash
gog mail watch --format json | while read -r msg; do
  subject=$(echo "$msg" | jq -r '.subject')
  from=$(echo "$msg" | jq -r '.from')
  if [[ "$subject" == *"状态"* ]]; then
    gog mail send --to "$from" --subject "Re: $subject" \
      --body "一切正常运行！"
  fi
done
```

## 练习

1. 启动邮件监控
2. 给自己发邮件，确认 watch 捕获到了
3. 写一个自动回复脚本
