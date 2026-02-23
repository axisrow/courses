---
title: "Monorepo 架构"
weight: 1
bookToc: true
---

# Monorepo 架构

## 简介

Pi Mono 组织为 monorepo——所有包都在一个 Git 仓库中，通过 npm workspaces 管理。

## 项目结构

```
pi-mono/
├── packages/
│   ├── ai/              # 统一 LLM API
│   ├── agent/           # 代理运行时
│   ├── coding-agent/    # CLI 编程助手
│   ├── mom/             # Slack 机器人
│   ├── tui/             # 终端 UI
│   ├── web-ui/          # Web 组件
│   └── pods/            # GPU pod 管理
├── package.json         # 根 workspace 配置
├── AGENTS.md            # 项目规则
├── CONTRIBUTING.md      # 贡献指南
└── test.sh              # 测试运行器
```

## 包依赖关系

```
coding-agent → agent → ai
                ↓
mom ──────────→ agent → ai
                        ↑
web-ui ─────────────────┘
tui（独立）
pods（独立）
```

## 开发命令

```bash
npm install          # 安装所有依赖
npm run build        # 构建所有包
npm run check        # 代码检查、格式化、类型检查
./test.sh            # 运行测试
```

## 重要提示

`npm run check` 需要先运行 `npm run build`，因为 web-ui 使用依赖项编译的 `.d.ts` 文件。

## 总结

- Pi Mono 是使用 npm workspaces 的 monorepo
- 7 个包有清晰的依赖关系
- 统一的构建和测试系统
