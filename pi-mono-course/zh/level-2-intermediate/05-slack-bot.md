---
title: "Slack 机器人（Mom）"
weight: 5
bookToc: true
---

# Slack 机器人（Mom）

## 简介

**Mom**（Master Of Mischief）是一个基于 LLM 的 Slack 机器人，可以执行命令、处理文件和自动化工作流程。Mom 自己安装所需工具并自主管理环境。

## 特性

- **自管理** — 自己安装工具和配置环境
- **Bash 访问** — 执行任何命令
- **Docker 沙箱** — 安全隔离
- **工作记忆** — 跨会话记住上下文
- **CLI 工具创建** — 为重复任务编写自定义脚本

## 安装

```bash
npm install @mariozechner/pi-mom
```

## Slack 设置

1. 在 https://api.slack.com/apps 创建应用
2. 启用 **Socket Mode**
3. 添加 Bot Token Scopes：`chat:write`、`channels:history`、`im:history` 等
4. 订阅事件：`app_mention`、`message.im`
5. 将应用安装到 workspace

## 快速开始

```bash
export MOM_SLACK_APP_TOKEN=xapp-...
export MOM_SLACK_BOT_TOKEN=xoxb-...
export ANTHROPIC_API_KEY=sk-ant-...

# Docker 沙箱（推荐）
docker run -d --name mom-sandbox -v $(pwd)/data:/workspace alpine:latest tail -f /dev/null

# 运行
mom --sandbox=docker:mom-sandbox ./data
```

## 总结

- Mom 是基于 Pi 的自管理 Slack 机器人
- 在 Docker 沙箱中运行以确保安全
- 自己为你的任务创建工具
