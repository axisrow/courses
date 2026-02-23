---
title: "初次环顾"
weight: 5
bookToc: true
---

# 初次环顾

## 欢迎来到你的新工作室

ACFS 安装完成后，你会看到一个彩色的终端界面。让我们看看你有什么。

### 终端现在不一样了

终端现在使用 **Powerlevel10k** — 一个漂亮的主题，显示有用的信息：
- 你在哪个文件夹
- 是否在 Git 仓库中
- 上一条命令花了多长时间

### 试试这些命令

```bash
# 查看安装了什么
acfs doctor
```

检查一切是否安装正确。绿色表示正常！

```bash
# 启动入门教程
onboard
```

打开内置教程，带你了解基础知识。

### 认识你的 AI 代理

你有三个 AI 编程助手。试着打个招呼：

```bash
# Claude Code（Anthropic 出品）
cc "你好，你能做什么？"

# Codex CLI（OpenAI 出品）
cod "你好，你能做什么？"

# Gemini CLI（Google 出品）
gmi "你好，你能做什么？"
```

> **注意**：每个代理都需要 API 密钥。安装程序会指导你设置。

### Tmux 安全网

你的 VPS 使用 **tmux** — 即使网络断开，工作也会继续运行。就像游戏的自动保存。

```bash
# 查看活跃的 tmux 会话
tmux list-sessions
```

### 关键要点

安装后，用 `acfs doctor` 验证一切正常，`onboard` 开始学习，`cc`、`cod` 或 `gmi` 与 AI 代理对话。Tmux 保证断线也不丢失工作。
