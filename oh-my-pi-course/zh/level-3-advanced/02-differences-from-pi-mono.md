---
title: "与 pi-mono 的区别"
level: 3
lesson: 2
lang: zh
tags: [pi-mono, fork, 区别, 比较]
---

# 与 pi-mono 的区别

## 介绍

OMP 是 pi-mono 的 fork，有大量新增功能。

## 新工具

| 功能 | pi-mono | OMP |
|------|---------|-----|
| Hashline 编辑 | ❌ | ✅ |
| Commit 工具 | ❌ | ✅ |
| Python 工具 (IPython) | ❌ | ✅ |
| LSP 集成 (40+ 语言) | ❌ | ✅ |
| TTSR (触发式规则) | ❌ | ✅ |
| Task 工具 (子代理) | ❌ | ✅ |
| 代码审查 (/review) | ❌ | ✅ |
| Todo 工具 | ❌ | ✅ |
| Ask 工具 | ❌ | ✅ |
| 浏览器 (14 隐身脚本) | ❌ | ✅ |
| SSH 工具 | ❌ | ✅ |
| 图像生成 | ❌ | ✅ |

## 原生引擎

pi-mono 使用外部工具（ripgrep、bash）。OMP 包含 7,500 行 Rust N-API 实现内置 grep、shell、语法高亮等模块。

## 通用配置发现

OMP 从 8 个工具加载配置：Claude Code、Cursor、Windsurf、Gemini、Codex、Cline、GitHub Copilot、VS Code。

## 扩展的服务商支持

- 更多服务商 (30+)
- 多凭证轮询
- Cursor 服务商
- 模型角色 (smol, slow, plan, commit)

## TUI

- 65+ 主题
- Powerline 底栏状态显示
- 自动会话标题
- LSP 状态
- Todo 面板 (Ctrl+T)

## 总结

OMP 显著扩展了 pi-mono：hashline、原生引擎、子代理、LSP、数十个新工具和服务商。
