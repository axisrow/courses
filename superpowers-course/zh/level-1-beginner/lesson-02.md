---
title: "安装 Superpowers"
level: 1
lesson: 2
lang: zh
---

# 安装 Superpowers

## 简介

如何在 Claude Code、Cursor、Codex 和 OpenCode 中安装 Superpowers。

## 安装方法

### Claude Code（推荐）

```bash
# 步骤 1：添加市场
/plugin marketplace add obra/superpowers-marketplace

# 步骤 2：安装插件
/plugin install superpowers@superpowers-marketplace
```

### Cursor

在 Cursor Agent 聊天中：
```
/plugin-add superpowers
```

### Codex

告诉 Codex：
```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

### OpenCode

告诉 OpenCode：
```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

## 验证安装

启动新会话，让代理规划一些功能：
```
帮我规划一个新功能
```

如果 Superpowers 正常工作，代理会开始提问而不是直接编码。

## 更新

```bash
/plugin update superpowers
```

## 总结

- 安装方式取决于平台
- Claude Code 和 Cursor — 通过市场安装
- Codex 和 OpenCode — 手动安装
- 通过让代理规划功能来验证安装
