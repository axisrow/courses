---
title: "贡献"
weight: 5
bookToc: true
---

# 贡献

## 简介

Pi Mono 是 MIT 许可下的开源项目。本课解释如何贡献。

## 开始

### 第1步：克隆仓库

```bash
git clone https://github.com/badlogic/pi-mono.git
cd pi-mono
```

### 第2步：安装依赖

```bash
npm install
```

### 第3步：构建项目

```bash
npm run build
```

### 第4步：运行测试

```bash
./test.sh
```

## 项目规则

学习这些文件：
- **CONTRIBUTING.md** — 贡献指南
- **AGENTS.md** — 项目规则（面向人类和代理）

## 工作流程

1. 创建 feature 分支
2. 进行更改
3. 运行 `npm run check`
4. 运行测试
5. 创建 Pull Request

## 从源码运行 Pi

```bash
./pi-test.sh    # 从源代码运行 pi
```

## 测试结构

依赖 LLM API 密钥的测试在未设置密钥时会被跳过，允许在不配置提供商的情况下运行基本测试。

## 社区

- [Discord](https://discord.com/invite/3cU7Bz4UPx) — 主要交流渠道
- GitHub Issues — 错误和建议
- Pull Requests — 代码贡献

## 总结

- Pi Mono 欢迎贡献
- 遵循 CONTRIBUTING.md 和 AGENTS.md
- 使用 Discord 提问
