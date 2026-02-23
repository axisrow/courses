---
title: "掌握 Tmux 持久会话"
weight: 6
bookToc: true
---

# 掌握 Tmux 持久会话

## 为什么 Tmux 很重要

关上笔记本或 WiFi 断了，普通 SSH 会话就死了 — 正在运行的一切都会停止。**Tmux** 完美解决这个问题。

### 基础概念

把 tmux 想象成 VPS 上的多个桌面：

- **会话（Sessions）** — 独立的工作空间
- **窗口（Windows）** — 像浏览器的标签页
- **面板（Panes）** — 像分屏

### 基本命令

```bash
# 创建命名会话
tmux new -s mywork

# 分离（会话在后台继续运行）
# 按：Ctrl+B，然后 D

# 列出所有会话
tmux ls

# 重新连接会话
tmux attach -t mywork
```

### ACFS 的 Tmux 配置

ACFS 预配置了 tmux：
- 启用鼠标支持（可以点击面板）
- 更好的快捷键
- 显示有用信息的状态栏

### 分屏

```bash
# 水平分割（上/下）
Ctrl+B，然后 "

# 垂直分割（左/右）
Ctrl+B，然后 %

# 在面板间切换
Ctrl+B，然后方向键
```

### 实际工作流

```
会话 "coding"            会话 "monitoring"
├── 窗口 1：代理 1       ├── 窗口 1：日志
├── 窗口 2：代理 2       └── 窗口 2：系统状态
└── 窗口 3：测试
```

### 关键要点

Tmux 在断线时保持工作。记住 `tmux new -s 名称`、`Ctrl+B D` 分离、`tmux attach -t 名称` 重连。这是你的安全网。
