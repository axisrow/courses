---
title: "Gmail 深入"
weight: 6
bookToc: true
---

# Gmail 深入

## 搜索邮件

```bash
gog mail search "from:boss@company.com"
gog mail search "subject:会议 after:2025-01-01"
gog mail search "has:attachment filename:pdf"
gog mail search "is:unread label:INBOX"
```

## 标签管理

```bash
gog mail labels
gog mail label add "项目A" MESSAGE_ID
gog mail label remove "项目A" MESSAGE_ID
```

## 批量操作

```bash
gog mail archive --older-than 30d
gog mail mark-read --label "通知"
gog mail delete --search "from:spam@example.com"
```

## 附件

```bash
gog mail attachments MESSAGE_ID
gog mail download MESSAGE_ID -o ./attachments/
gog mail send --to user@gmail.com --subject "报告" --attach report.pdf
```

## 草稿

```bash
gog mail draft --to user@gmail.com --subject "草稿" --body "稍后发送"
gog mail drafts list
gog mail draft send DRAFT_ID
```

## 练习

1. 搜索所有带附件的邮件
2. 给几封邮件添加同一个标签
3. 归档 30 天前的已读邮件
