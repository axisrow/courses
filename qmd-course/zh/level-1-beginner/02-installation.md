---
title: "安装 QMD"
weight: 2
bookToc: true
---

# 安装 QMD

## 前提条件

安装前请确保你有：

- **Node.js** 22 或更新版本
- **macOS 用户**：通过 Homebrew 安装 SQLite（`brew install sqlite`）

## 检查 Node.js 版本

打开终端，输入：

```sh
node --version
```

应显示 `v22.0.0` 或更高。如果不是，请访问 [nodejs.org](https://nodejs.org) 安装最新版本。

## 安装 QMD

```sh
npm install -g @tobilu/qmd
```

或使用 Bun：

```sh
bun install -g @tobilu/qmd
```

## 验证安装

```sh
qmd status
```

## 无需安装即可试用

```sh
npx @tobilu/qmd status
```

## AI 模型

QMD 使用三个本地 AI 模型，首次使用时自动下载：

| 模型 | 用途 | 大小 |
|------|------|------|
| EmbeddingGemma | 理解文档含义 | ~300 MB |
| Qwen3 Reranker | 按相关性排序 | ~640 MB |
| QMD Query Expansion | 改进搜索查询 | ~1.1 GB |

模型存储在 `~/.cache/qmd/models/`。

## 下一步

QMD 已安装——让我们添加第一个文档集合！
