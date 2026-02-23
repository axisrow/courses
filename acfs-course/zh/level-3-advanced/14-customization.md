---
title: "自定义你的 ACFS 环境"
weight: 14
bookToc: true
---

# 自定义你的 ACFS 环境

## 打造你自己的

ACFS 带有合理的默认设置，但一切都可以自定义。你的自定义在更新后保留。

### 关键配置文件

| 文件 | 控制什么 |
|------|---------|
| `~/.acfs/` | 主 ACFS 配置目录 |
| `~/.zshrc` | Shell 行为和别名 |
| `~/.tmux.conf` | Tmux 布局和快捷键 |

### 环境变量

```bash
export ACFS_HOME=~/.acfs
export ACFS_LOG_DIR=/var/log/acfs
export TARGET_USER=ubuntu
```

### 安装模式

- **`--mode vibe`** — 最大速度。启用危险标志。适用于一次性 VPS。
- 默认模式 — 更保守，有确认提示。

### 代理配置

```bash
# Claude Code 设置在：
~/.acfs/claude/settings.json
```

### 向导网站

访问 [agent-flywheel.com](https://agent-flywheel.com) 获取可视化设置体验 — 13步引导向导。

### 安全注意事项

**Vibe 模式** 启用的标志：
- `--dangerously-skip-permissions`（Claude）
- `--dangerously-bypass-approvals-and-sandbox`（Codex）
- `--yolo`（Gemini）

仅用于：
- ✅ 一次性 VPS
- ✅ 个人实验
- ❌ 绝不用于生产服务器
- ❌ 绝不用于共享基础设施

### 关键要点

ACFS 通过环境变量、配置文件和安装模式高度可定制。一次性服务器上用 vibe 模式追求速度，生产环境绝不使用。
