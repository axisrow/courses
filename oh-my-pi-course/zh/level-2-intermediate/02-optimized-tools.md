---
title: "优化工具"
level: 2
lesson: 2
lang: zh
tags: [工具, python, lsp, commit, 浏览器]
---

# 优化工具

## 介绍

OMP 包含一套强大的内置工具，远超基本功能。

## Commit 工具

AI 驱动的提交生成：

```bash
omp commit              # 交互模式
omp commit --push       # 提交 + 推送
omp commit --dry-run    # 预览
```

功能：拆分提交、hunk 级暂存、changelog 生成。

## Python 工具

持久化 IPython 内核：

```bash
omp setup python  # 安装依赖
```

辅助函数：`lines()`、`insert_at()`、`delete_lines()`、搜索、shell 命令。

## LSP 集成

- 写入时格式化（rustfmt、prettier、gofmt 等）
- 每次修改后的诊断
- 开箱支持 40+ 语言
- Hover 文档、符号搜索

## 浏览器工具

带 14 个隐身脚本的无头浏览器：

- 导航、点击、截图
- 无障碍快照
- 阅读器模式提取内容

## Task 工具（子代理）

6 个内置代理用于并行工作：explore、plan、designer、reviewer、task、quick_task。

## Web 搜索和获取

多服务商：Exa、Jina、Perplexity、Anthropic、Gemini 等。

## 完整工具列表

`ask`、`bash`、`python`、`calc`、`ssh`、`edit`、`find`、`grep`、`lsp`、`notebook`、`read`、`browser`、`task`、`todo_write`、`fetch`、`web_search`、`write`

## 总结

OMP 为各种任务提供丰富的工具集 — 从提交到浏览器自动化。
