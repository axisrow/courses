---
title: "为 GSD 做贡献"
level: 3
lesson: 5
language: zh
tags: [gsd, 贡献, 开源]
---

# 为 GSD 做贡献

## 介绍

GSD 是一个 MIT 许可的开源项目。你可以进行更改、修复 bug 和添加功能。

## 操作指南

### 开始

```bash
git clone https://github.com/glittercowboy/get-shit-done.git
cd get-shit-done
node bin/install.js --claude --local
```

这会在本地安装 GSD 用于测试更改。

### 项目结构

```
get-shit-done/
├── bin/
│   └── install.js          # 安装程序
├── prompts/
│   └── claude/
│       └── commands/gsd/    # 斜杠命令
├── docs/
│   └── USER-GUIDE.md       # 文档
└── README.md
```

### 可以贡献什么

- **命令** — 新的斜杠命令或改进现有命令
- **文档** — 修复、翻译、示例
- **Bug 修复** — 修复问题
- **运行时** — 支持新的 AI 代理
- **测试** — 提高覆盖率

### 流程

1. Fork 仓库
2. 创建分支：`git checkout -b feature/my-feature`
3. 进行更改
4. 通过 `node bin/install.js --claude --local` 本地测试
5. 创建 Pull Request

### 社区

- [Discord](https://discord.gg/5JJgD5svVS) — 问题和讨论
- [GitHub Issues](https://github.com/glittercowboy/get-shit-done/issues) — bug 和建议
- [Twitter/X](https://x.com/gsd_foundation) — 新闻

## 示例

```bash
# 测试命令更改
cd get-shit-done
# 编辑 prompts/claude/commands/gsd/some-command.md
node bin/install.js --claude --local
# 打开 Claude Code 测试 /gsd:some-command
```

## 总结

- GSD 是开源的（MIT）
- 克隆并本地安装用于开发
- 可以贡献命令、文档、修复
- 社区在 Discord
- 通过标准 GitHub 流程提交 PR
