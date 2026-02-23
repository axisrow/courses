---
title: "安装 CodeMachine"
weight: 2
bookToc: true
---

# 安装 CodeMachine

## 准备工作

安装前，确保你有：

1. **Node.js**（18 或更高版本）— 在电脑上运行 JavaScript 的程序
2. **终端** — 文本界面（Mac 的 Terminal，Windows 的 PowerShell）
3. **AI 引擎** — 至少一个：Claude Code、Codex CLI 或 Cursor

> **没有 Node.js？** 访问 [nodejs.org](https://nodejs.org) 下载最新版本。

## 安装步骤

打开终端，输入：

```bash
npm i -g codemachine
```

`-g` 表示「全局」——你可以在任何文件夹中使用它。

## 验证安装

```bash
codemachine --version
```

你应该看到版本号（如 `0.8.0`）。

## 快捷命令

可以用 `cm` 代替 `codemachine`：

```bash
cm
```

## 重要规则

CodeMachine 必须在**项目文件夹**内运行，不能在主目录：

```bash
cd ~/my-project
codemachine
```

或指定目录：

```bash
codemachine --dir ~/my-project
```

## 总结

- 安装：`npm i -g codemachine`
- 验证：`codemachine --version`
- 快捷命令：`cm`
- 始终在项目文件夹内运行

> **下一课：** 创建第一个项目，探索界面。
