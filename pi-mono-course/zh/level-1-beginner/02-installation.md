---
title: "安装 Pi Mono"
weight: 2
bookToc: true
---

# 安装 Pi Mono

## 简介

在本课中，我们将安装 Pi Mono 并设置工作环境。

## 要求

- **Node.js** 18 或更高版本
- **npm**（随 Node.js 一起安装）
- 终端（命令行）

## 分步安装

### 第1步：安装 Node.js

从 [nodejs.org](https://nodejs.org) 下载并安装 Node.js。验证安装：

```bash
node --version
npm --version
```

### 第2步：安装编程代理

```bash
npm install -g @mariozechner/pi-coding-agent
```

### 第3步：设置 API 密钥

使用 AI 模型需要密钥。例如 Anthropic：

```bash
export ANTHROPIC_API_KEY=sk-ant-你的密钥
```

或使用内置认证：

```bash
pi
/login
```

### 第4步：验证安装

```bash
pi --help
```

## 总结

- 安装了 Node.js 和 npm
- 全局安装了 Pi 编程代理
- 配置了 LLM 提供商的 API 密钥
