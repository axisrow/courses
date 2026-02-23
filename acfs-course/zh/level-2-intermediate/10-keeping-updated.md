---
title: "保持系统更新"
weight: 10
bookToc: true
---

# 保持系统更新

## 为什么要更新

ACFS 在积极开发中。更新带来新功能、安全修复和改进。

### 更新 ACFS

```bash
acfs update
```

这条命令：
- 拉取最新 ACFS 代码
- 更新配置文件
- 刷新工具版本
- 保留你的自定义设置

### 检查系统健康

```bash
acfs doctor
```

定期运行。检查：
- 所有工具已安装且正常
- 版本是最新的
- 配置正确

### 更新单个工具

```bash
bun upgrade       # JavaScript
rustup update     # Rust
uv self update    # Python
```

### 固定版本

对重要项目，可以固定 ACFS 版本：

```bash
ACFS_REF=v0.5.0 curl -fsSL "..." | bash -s -- --yes --mode vibe
```

### 关键要点

`acfs update` 获取最新改进。`acfs doctor` 检查系统健康。关键工作用 `ACFS_REF` 固定版本。
