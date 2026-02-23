---
title: "贡献代码"
level: 3
lesson: 5
lang: zh
tags: [贡献, 开源, PR, 开发]
---

# 为 Oh My Pi 贡献代码

## 介绍

OMP 是 MIT 许可证下的开源项目。以下是参与贡献的方法。

## 开始

1. 在 GitHub 上 Fork 仓库
2. 克隆你的 Fork
3. 创建分支

```bash
git clone https://github.com/YOUR_USERNAME/oh-my-pi.git
cd oh-my-pi
git checkout -b feature/my-improvement
bun install
```

## 贡献类型

### Bug 报告
- 使用 GitHub Issues
- 包括 OMP 版本、操作系统、终端信息
- 附上 `~/.omp/logs/` 中的日志

### 新功能
- 在 Issue 或 Discord 中讨论想法
- 遵循现有代码模式

### 新服务商
- 在 `packages/ai/` 中添加配置

### 自定义工具
- 在 `packages/coding-agent/src/tools/` 中创建

### 主题
- 在 `packages/coding-agent/themes/` 中添加 JSON 文件

### 文档
- `docs/` 文件夹

## Pull Request 流程

1. 确保代码能构建：`bun run build`
2. 运行测试
3. 使用约定式提交
4. 在 PR 中描述更改

```bash
# 使用 OMP 来提交！
omp commit --push
```

## 资源

- [DEVELOPMENT.md](https://github.com/can1357/oh-my-pi/blob/main/packages/coding-agent/DEVELOPMENT.md)
- [Discord](https://discord.gg/4NMW9cdXZa)
- [CHANGELOG.md](https://github.com/can1357/oh-my-pi/blob/main/packages/coding-agent/CHANGELOG.md)

## 许可证

MIT。Copyright (c) 2025 Mario Zechner，2025-2026 Can Bölük。

## 总结

欢迎为 OMP 贡献代码 — 从 Bug 报告到新功能。使用 GitHub Issues 和 PR，遵循约定式提交。
