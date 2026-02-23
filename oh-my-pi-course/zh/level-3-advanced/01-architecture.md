---
title: "架构 (TypeScript + Rust + Bun)"
level: 3
lesson: 1
lang: zh
tags: [架构, typescript, rust, bun, 单体仓库]
---

# Oh My Pi 架构

## 介绍

OMP 是一个结合 TypeScript、Rust 和 Bun 的单体仓库，追求最大性能。

## 技术栈

- **TypeScript** — 核心逻辑、TUI、代理、SDK
- **Rust** — 通过 N-API 的原生模块（约 7,500 行）
- **Bun** — 替代 Node.js 的运行时（更快，原生 TypeScript 支持）

## 单体仓库包

| 包 | 描述 |
|---|------|
| `@oh-my-pi/pi-ai` | 多服务商 LLM 客户端 |
| `@oh-my-pi/pi-agent-core` | 带工具调用的代理运行时 |
| `@oh-my-pi/pi-coding-agent` | 编程代理 CLI 和 SDK |
| `@oh-my-pi/pi-tui` | 终端 UI 库 |
| `@oh-my-pi/pi-natives` | N-API 绑定 (Rust) |
| `@oh-my-pi/omp-stats` | 统计仪表板 |
| `@oh-my-pi/pi-utils` | 工具函数 |

## 原生引擎 (Rust)

| 模块 | 行数 | 功能 | 依赖 |
|------|------|------|------|
| grep | ~1,300 | 文件正则搜索 | ripgrep 内部 |
| shell | ~1,025 | 内嵌 bash 执行 | brush-shell |
| text | ~1,280 | ANSI 感知文本处理 | unicode-width |
| keys | ~1,300 | Kitty 键盘解析器 | phf |
| highlight | ~475 | 语法高亮 | syntect |
| glob | ~340 | 文件发现 | ignore, globset |
| task | ~350 | 工作调度器 | tokio, napi |
| ps | ~290 | 进程管理 | libc |
| prof | ~250 | 性能分析器 | inferno |
| image | ~150 | 图像处理 | image |
| clipboard | ~95 | 剪贴板访问 | arboard |
| html | ~50 | HTML → Markdown | html-to-markdown-rs |

平台：linux-x64、linux-arm64、darwin-x64、darwin-arm64、win32-x64。

## 总结

OMP 的架构结合了 TypeScript 的便利性和 Rust 的高性能，使用 Bun 作为快速运行时。
