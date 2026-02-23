---
title: "从源码构建"
level: 3
lesson: 4
lang: zh
tags: [构建, 开发, 源码, bun, rust]
---

# 从源码构建

## 介绍

如果你想修改 OMP 或参与开发，需要从源码构建项目。

## 要求

- [Bun](https://bun.sh) >= 1.3.7
- [Rust](https://rustup.rs/)（原生模块）
- Git

## 克隆

```bash
git clone https://github.com/can1357/oh-my-pi.git
cd oh-my-pi
```

## 安装依赖

```bash
bun install
```

## 构建 Rust 模块

```bash
cd crates/pi-natives
cargo build --release
```

## 构建 TypeScript

```bash
bun run build
```

## 运行本地版本

```bash
bun run packages/coding-agent/src/cli.ts
```

## 通过脚本安装（源码模式）

```bash
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --source --ref main
```

## 项目结构

```
oh-my-pi/
├── packages/
│   ├── ai/              # LLM 客户端
│   ├── agent/           # 代理运行时
│   ├── coding-agent/    # CLI + SDK
│   ├── tui/             # 终端 UI
│   ├── natives/         # N-API 绑定
│   ├── stats/           # 统计仪表板
│   └── utils/           # 工具函数
├── crates/
│   ├── pi-natives/      # Rust N-API
│   ├── brush-core-vendored/
│   └── brush-builtins-vendored/
├── scripts/             # 安装脚本
└── docs/                # 文档
```

## 调试

在 OMP 中使用 `/debug` 进行调试和性能分析。日志写入 `~/.omp/logs/`，每日轮转。

## 总结

构建 OMP 需要 Bun 和 Rust。单体仓库组织为 packages/（TypeScript）和 crates/（Rust）。
