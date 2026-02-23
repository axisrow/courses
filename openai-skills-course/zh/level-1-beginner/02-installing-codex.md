---
title: "安装Codex"
weight: 2
bookToc: true
---

# 安装Codex

## 简介

Codex是OpenAI的AI代理，在命令行（CLI）中运行。它使用Skills来执行任务。本课将指导您在计算机上安装Codex。

## 要求

- macOS、Windows或Linux计算机
- 已安装Node.js（18版本或更新）
- 拥有API密钥的OpenAI账户

## 分步安装

### 第1步：检查Node.js

打开终端并输入：

```bash
node --version
```

如果版本低于18或未安装Node.js，请从[nodejs.org](https://nodejs.org)下载。

### 第2步：安装Codex

```bash
npm install -g @openai/codex
```

### 第3步：设置API密钥

```bash
export OPENAI_API_KEY="您的密钥"
```

要在会话之间保持密钥，请将此行添加到`~/.bashrc`或`~/.zshrc`。

### 第4步：验证安装

```bash
codex --help
```

您应该看到可用命令列表。

## 技能存储位置

安装后，Codex创建主目录：

```
~/.codex/
└── skills/     — 技能安装在这里
```

系统技能（`.system`）内置于Codex，安装后立即可用。

## 总结

- Codex通过npm安装
- 需要OpenAI API密钥
- 技能存储在`~/.codex/skills/`
- 系统技能安装后立即可用
