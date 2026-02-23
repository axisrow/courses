---
title: "安装"
level: 1
lesson: 2
lang: zh
tags: [安装, bun, npm]
---

# 安装 Oh My Pi

## 介绍

有多种方式安装 OMP，推荐使用 Bun。

## 方式 1：通过 Bun（推荐）

需要 [Bun](https://bun.sh) >= 1.3.7。

```bash
# 安装 Bun
curl -fsSL https://bun.sh/install | bash

# 安装 OMP
bun install -g @oh-my-pi/pi-coding-agent
```

## 方式 2：安装脚本

**Linux / macOS：**

```bash
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh
```

**Windows (PowerShell)：**

```powershell
irm https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.ps1 | iex
```

## 方式 3：通过 mise

```bash
mise use -g github:can1357/oh-my-pi
```

## 方式 4：手动下载

从 [GitHub Releases](https://github.com/can1357/oh-my-pi/releases/latest) 下载。

## 验证安装

```bash
omp --version
```

## 其他选项

```bash
# 安装特定版本
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --binary --ref v3.20.1

# 从源码安装
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --source --ref main
```

自定义安装目录：`PI_INSTALL_DIR`。

## 总结

OMP 可通过 Bun、脚本、mise 或手动安装。推荐 Bun —— 快速简单。
