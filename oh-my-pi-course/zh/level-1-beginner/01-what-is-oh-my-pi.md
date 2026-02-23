---
title: "什么是 Oh My Pi"
level: 1
lesson: 1
lang: zh
tags: [介绍, 概述]
---

# 什么是 Oh My Pi

## 介绍

Oh My Pi（OMP）是一个直接在终端中运行的 AI 编程助手。它是 Mario Zechner 的 [pi-mono](https://github.com/badlogic/pi-mono) 的 fork，由 Can Bölük 扩展开发。

## 功能概览

OMP 是一个功能齐全的终端 AI 编程环境：

- **交互式终端界面** — 在终端中与 AI 对话
- **内置工具** — 文件编辑、搜索、grep、bash、Python、浏览器
- **会话分支** — 保存并返回对话中的任何节点
- **可扩展性** — 自定义命令、钩子、技能、工具
- **多服务商** — Anthropic、OpenAI、Google、xAI、Groq 等数十个

## 与 pi-mono 的主要区别

OMP 在 pi-mono 基础上新增：

- **Hashline 编辑** — 每行唯一哈希锚点，杜绝"字符串未找到"错误
- **Rust 原生引擎** — 7,500 行 Rust 代码实现 grep、shell、语法高亮
- **LSP 集成** — 支持 40+ 语言的格式化和诊断
- **Commit 工具** — AI 驱动的提交生成，支持 hunk 级暂存
- **Python 工具** — 持久化 IPython 内核
- **TTSR** — 仅在需要时触发的规则（激活前零上下文消耗）
- **子代理** — 并行任务执行
- **65+ 主题**

## 快速示例

```bash
omp
> 列出 src/ 中所有的 .ts 文件
```

## 总结

Oh My Pi 是一个基于 pi-mono 构建的强大终端 AI 助手，包含大量增强功能。接下来的课程将指导你安装和使用它。
