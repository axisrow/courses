---
title: "安装 RAPTOR"
weight: 3
bookToc: true
---

## 安装 RAPTOR

### 前提条件

开始之前，你需要:

- 运行 Linux 或 macOS 的电脑（Windows 可通过 WSL 使用）
- 已安装 **Claude Code**（从 https://claude.ai/download 下载）
- 用于 AI 分析的 **Anthropic API 密钥**
- **Git** 用于下载代码

### 分步安装

#### 方式一:手动安装

```bash
# 下载 RAPTOR
git clone https://github.com/gadievron/raptor.git
cd raptor

# 启动 Claude Code
claude

# 在 Claude 中安装依赖
"Install dependencies from requirements.txt"
"Install semgrep"
"Set my ANTHROPIC_API_KEY to 你的密钥"
```

#### 方式二:DevContainer（推荐初学者使用）

DevContainer 预装了所有内容。在 VS Code 中打开 RAPTOR 文件夹并选择 **Dev Container: Open Folder in Container**。

或手动构建:

```bash
docker build -f .devcontainer/Dockerfile -t raptor-devcontainer:latest .
```

### 会安装什么？

- **Semgrep** — 静态分析引擎
- **CodeQL** — GitHub 的语义代码分析
- **AFL++** — 模糊测试工具
- **rr debugger** — 记录-回放调试器

### 核心要点

最简单的开始方式是使用 DevContainer——它自动处理所有依赖。如果你偏好手动设置，请按上述步骤操作。
