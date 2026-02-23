---
title: "安装Shannon"
weight: 2
bookToc: true
---

# 安装Shannon

## 简介

在本课中，我们将安装运行Shannon所需的一切。

## 前提条件

1. **Docker** — 容器化系统（Shannon在容器中运行）
2. **Anthropic API密钥** — Shannon使用Claude AI进行分析

## 第1步：安装Docker

### macOS
下载并安装[Docker Desktop](https://docs.docker.com/get-docker/)。开箱即用。

### Windows
推荐使用WSL2：

```powershell
wsl --install
wsl --set-default-version 2
wsl --install Ubuntu-24.04
```

然后安装Docker Desktop，在设置中启用"Use the WSL 2 based engine"。

### Linux
按照[官方指南](https://docs.docker.com/get-docker/)安装Docker。可能需要`sudo`。

## 第2步：获取API密钥

1. 访问[console.anthropic.com](https://console.anthropic.com)
2. 注册或登录
3. 创建API密钥
4. 保存它

## 第3步：克隆Shannon

```bash
git clone https://github.com/KeygraphHQ/shannon.git
cd shannon
```

## 第4步：配置凭据

```bash
cat > .env << 'EOF'
ANTHROPIC_API_KEY=您的密钥
CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
EOF
```

## 第5步：验证

```bash
docker --version
```

看到Docker版本号就说明一切就绪！

## 总结

- 安装了Docker
- 获取了Anthropic API密钥
- 克隆了Shannon仓库
- 配置了凭据
