---
title: "安装 GSD"
level: 1
lesson: 2
language: zh
tags: [gsd, 安装, npx]
---

# 安装 GSD

## 介绍

GSD 通过一条 npx 命令安装。不需要克隆仓库或管理依赖。

## 操作指南

### 快速安装

```bash
npx get-shit-done-cc@latest
```

安装程序会询问：
1. **运行时** — Claude Code、OpenCode、Gemini 或全部
2. **位置** — 全局（所有项目）或本地（当前项目）

### 非交互式安装

```bash
npx get-shit-done-cc --claude --global    # Claude Code 全局
npx get-shit-done-cc --opencode --global  # OpenCode 全局
npx get-shit-done-cc --gemini --global    # Gemini CLI 全局
npx get-shit-done-cc --all --global       # 所有运行时
```

### 验证安装

打开 Claude Code 并输入：

```
/gsd:help
```

如果看到命令列表——安装成功。

## 示例

```bash
# 在当前项目安装 Claude Code 版本
npx get-shit-done-cc --claude --local

# 更新到最新版本
npx get-shit-done-cc@latest
```

## 总结

- 通过 `npx get-shit-done-cc@latest` 安装
- 选择运行时和位置（全局/本地）
- 通过 `/gsd:help` 验证
- 使用 `@latest` 更新
