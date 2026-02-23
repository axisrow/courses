---
title: "触发器与定时调度"
weight: 5
bookToc: true
---

# 触发器与定时调度

## 什么是触发器？

触发器是工作流的第一个节点，决定**何时**运行工作流。

## 触发器类型

### Manual Trigger
手动运行，适合测试。

### Schedule Trigger
定时运行：
- 每 5 分钟
- 每天早上 9 点
- 每周一
- 每月 1 号

**Cron 示例：**
```
0 9 * * *       → 每天 9:00
0 9 * * 1       → 每周一 9:00
*/30 * * * *    → 每 30 分钟
```

### Webhook
外部服务发送 HTTP 请求时触发。

1. 添加 **Webhook** 节点
2. 复制 URL
3. 在外部服务中配置该 URL

**用途：** 接收表单、GitHub/Stripe 通知等。

### 应用触发器
- **Gmail Trigger** — 新邮件
- **Slack Trigger** — 新消息
- **GitHub Trigger** — 新 Issue

## 激活工作流

触发器只在工作流**激活**时才生效：

1. 构建工作流
2. 打开右上角 **Active** 开关
3. 工作流将自动运行

## 轮询 vs Webhook

| 特点 | 轮询 | Webhook |
|------|------|---------|
| 原理 | n8n 定期检查 | 服务主动推送 |
| 速度 | 有延迟 | 即时 |
| 配置 | 更简单 | 需要 URL |

## 练习

1. 创建 **Schedule Trigger** 工作流（每分钟）
2. 添加 **HTTP Request** 获取时间：`http://worldtimeapi.org/api/timezone/UTC`
3. 激活并查看执行历史

## 小结

你已掌握触发器和定时调度。初级阶段完成！接下来进入中级——API 操作。
