---
title: "故障排除和最佳实践"
weight: 15
bookToc: true
---

# 故障排除和最佳实践

## 常见问题和解决方案

### 「命令未找到」

```bash
source ~/.zshrc    # 重新加载配置
exec zsh           # 或启动新 shell
```

### 「代理无法启动」

检查 API 密钥：

```bash
echo $ANTHROPIC_API_KEY  # Claude
echo $OPENAI_API_KEY     # Codex
echo $GOOGLE_API_KEY     # Gemini
```

### 「安装中途失败」

直接重新运行 — 安装程序是幂等的：

```bash
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/agentic_coding_flywheel_setup/main/install.sh" | bash -s -- --yes --mode vibe
```

### 「Tmux 会话消失了」

```bash
tmux ls  # 如果为空 — 服务器重启了？代码还在文件系统中，创建新会话。
```

### 运行诊断

```bash
acfs doctor        # 完整健康检查
which claude       # 显示路径
claude --version   # 显示版本
```

## 最佳实践

### 日常工作流
1. SSH 到 VPS
2. 重新连接 tmux：`tmux attach`
3. 用 NTM 管理代理
4. 每周运行 `acfs doctor`

### 项目工作流
1. 每个功能创建新分支
2. 通过 NTM 分配代理
3. Agent Mail 协调
4. 合并前用 UBS 扫描
5. 项目完成后运行 `cm reflect`

### 安全习惯
1. 大变更前做 VPS 快照
2. 绝不在生产服务器上用 vibe 模式
3. 部署前审查代理写的代码
4. 不要禁用 DCG 和 SLB
5. 频繁提交 — 这是你的撤销按钮

### 何时重新开始

有时最快的修复是全新开始：
1. 创建新 VPS
2. 运行 ACFS 安装程序
3. 克隆你的仓库
4. 30分钟后恢复工作

代码在 Git 里，VPS 是一次性的 — 这就是 ACFS 方法的美妙之处。

### 关键要点

大多数问题通过重新加载 shell 或重新运行安装程序解决。`acfs doctor` 做诊断。代码放 Git 里，VPS 保持一次性。
