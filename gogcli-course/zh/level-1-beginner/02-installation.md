---
title: "安装"
weight: 2
bookToc: true
---

# 安装 gogcli

## 系统要求

- macOS、Linux 或 Windows
- 终端（命令行）

## 安装方法

### macOS (Homebrew)

```bash
brew install gogcli
```

### Linux

```bash
curl -fsSL https://get.gogcli.dev | bash
```

### Windows

```powershell
winget install gogcli
```

### 从源码安装

```bash
go install github.com/gogcli/gog@latest
```

## 验证安装

```bash
gog version
gog help
```

## 练习

1. 选择适合你系统的方式安装 gogcli
2. 运行 `gog version` 确认安装成功
3. 运行 `gog help` 浏览可用命令
