---
title: "安装DeerFlow"
weight: 2
bookToc: true
---

# 安装DeerFlow

## 简介

在本课中，我们将逐步在您的计算机上安装DeerFlow。有两种方法：通过**Docker**（推荐）和手动安装。Docker是一个为应用程序创建隔离容器的程序——就像内部包含所有必需内容的"盒子"。

## 您需要什么

- 一台运行Windows、macOS或Linux的计算机
- 互联网连接
- AI提供商的API密钥（OpenAI、Anthropic、DeepSeek等）

> **API密钥**——一个唯一的密码，允许您的应用程序与AI服务通信。您可以从提供商的网站获取（例如platform.openai.com）。

## 方法1：Docker安装（推荐）

### 步骤1：安装Docker

1. 访问 [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. 下载适合您操作系统的Docker Desktop
3. 安装并启动Docker Desktop

### 步骤2：安装pnpm

```bash
npm install -g pnpm
```

### 步骤3：克隆仓库

```bash
git clone https://github.com/bytedance/deer-flow.git
cd deer-flow
```

### 步骤4：创建配置文件

```bash
make config
```

### 步骤5：设置API密钥

编辑`.env`文件：

```bash
OPENAI_API_KEY=sk-your-key-here
```

### 步骤6：启动DeerFlow

```bash
make docker-init    # 仅首次运行
make docker-start   # 启动所有服务
```

### 步骤7：在浏览器中打开

访问：**http://localhost:2026**

🎉 完成！DeerFlow正在运行。

## 方法2：本地安装

### 前提条件

- **Node.js 22+**
- **pnpm**
- **Python 3.12+**
- **uv** — Python包管理器
- **nginx**

```bash
make check          # 验证依赖
git clone https://github.com/bytedance/deer-flow.git
cd deer-flow
make config
# 在.env中编辑您的API密钥
make dev
```

## 服务管理

| 命令 | 说明 |
|------|------|
| `make docker-start` | 启动所有服务 |
| `make docker-stop` | 停止所有服务 |
| `make docker-restart` | 重启服务 |
| `make docker-logs` | 查看日志 |
| `make dev` | 本地启动 |

## 常见问题

- **"端口2026已被占用"** — 停止其他程序或更改端口
- **"Docker守护进程未运行"** — 启动Docker Desktop
- **"API密钥无效"** — 检查`.env`中的密钥

## 总结

- DeerFlow可以通过Docker（更简单）或本地方式安装
- 您需要AI提供商的API密钥
- Web界面地址：http://localhost:2026
- 使用`make`命令进行管理
