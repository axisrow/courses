---
title: "Building from Source"
level: 3
lesson: 4
lang: en
tags: [build, development, source, bun, rust]
---

# Building from Source

## Introduction

If you want to modify OMP or contribute, you'll need to build from source.

## Requirements

- [Bun](https://bun.sh) >= 1.3.7
- [Rust](https://rustup.rs/) (for native modules)
- Git

## Clone

```bash
git clone https://github.com/can1357/oh-my-pi.git
cd oh-my-pi
```

## Install Dependencies

```bash
bun install
```

## Build Rust Modules

```bash
cd crates/pi-natives
cargo build --release
```

## Build TypeScript

```bash
bun run build
```

## Run Local Version

```bash
bun run packages/coding-agent/src/cli.ts
```

## Install via Script (source mode)

```bash
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --source --ref main
```

## Project Structure

```
oh-my-pi/
├── packages/
│   ├── ai/              # LLM client
│   ├── agent/           # Agent runtime
│   ├── coding-agent/    # CLI + SDK
│   ├── tui/             # Terminal UI
│   ├── natives/         # N-API bindings
│   ├── stats/           # Stats dashboard
│   └── utils/           # Utilities
├── crates/
│   ├── pi-natives/      # Rust N-API
│   ├── brush-core-vendored/
│   └── brush-builtins-vendored/
├── scripts/             # Install scripts
└── docs/                # Documentation
```

## Debugging

Use `/debug` in OMP for debugging and profiling tools. Logs are written to `~/.omp/logs/` with daily rotation.

## Summary

Building OMP requires Bun and Rust. The monorepo is organized into packages/ (TypeScript) and crates/ (Rust).
