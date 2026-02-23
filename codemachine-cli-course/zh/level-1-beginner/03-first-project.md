---
title: "你的第一个项目"
weight: 3
bookToc: true
---

# 你的第一个项目

## 创建项目文件夹

```bash
mkdir my-first-workflow
cd my-first-workflow
```

## 启动 CodeMachine

```bash
codemachine
```

首次运行时，CodeMachine 会在项目内创建 `.codemachine` 文件夹，存储所有配置。

## .codemachine 文件夹

```
my-first-workflow/
└── .codemachine/
    ├── config/          ← 代理和工作流设置
    ├── prompts/         ← AI 代理的指令
    ├── inputs/          ← 项目规格说明
    └── logs/            ← 执行日志
```

## 文本界面（TUI）

启动后，你会在终端看到文本界面，显示：

- 当前工作流状态
- 活跃的代理
- 已完成步骤的时间线

## 快捷键

| 按键 | 功能 |
|------|------|
| Tab | 显示/隐藏时间线面板 |
| Shift+Tab | 切换自主模式 |
| P | 暂停工作流 |
| H | 查看历史 |
| ↑ / ↓ | 导航 |
| Escape | 停止（需确认） |

## Ali 工作流构建器

CodeMachine 内置了 **Ali** 工作流。Ali 是一个友好的助手，通过提问帮你创建第一个工作流并生成所需文件。

## 总结

- 创建项目文件夹并运行 `codemachine`
- `.codemachine` 文件夹自动创建
- TUI 提供终端中的可视化界面
- Ali 帮你交互式创建工作流

> **下一课：** 理解工作流。
