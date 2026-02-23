---
title: "运行 ACFS 安装程序"
weight: 4
bookToc: true
---

# 运行 ACFS 安装程序

## 神奇的命令

通过 SSH 连接到 VPS 后，运行这一条命令：

```bash
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/agentic_coding_flywheel_setup/main/install.sh" | bash -s -- --yes --mode vibe
```

### 这做了什么？

用简单的话来说：

- `curl` — 从互联网下载文件
- `|` — 把它发送给……
- `bash` — 执行命令的程序
- `--yes` — 自动回答所有问题「是」
- `--mode vibe` — 以最快速度安装一切

### 安装了什么（30+ 工具）

安装程序会设置：

1. **漂亮的终端** — 彩色的，有便捷的快捷键
2. **编程语言** — Python、JavaScript、Rust、Go
3. **三个 AI 编程代理** — Claude Code、Codex CLI、Gemini CLI
4. **10个协调工具** — 管理多个 AI 代理
5. **云端工具** — 部署项目
6. **开发者工具** — 搜索、编辑和管理代码

### 需要多长时间？

大约 **30 分钟**。你可以看着它工作，也可以去喝杯咖啡。

### 如果失败了怎么办？

安装程序是 **幂等的** — 意思是可以安全地重新运行。如果网络断了或出了问题，只需再运行同样的命令。它会从中断的地方继续。

### 关键要点

一条命令安装一切。大约30分钟。失败了就再运行一次 — 设计上就是可以重复运行的。
