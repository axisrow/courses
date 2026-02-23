---
title: "安装与首次启动"
weight: 2
bookToc: true
---

# 安装与首次启动

## 准备工作

| 资源 | 最低要求 |
|------|---------|
| **CPU** | 2 核 |
| **内存** | 6 GB |
| **软件** | 已安装 Docker 和 Docker Compose |

> **什么是 Docker？** Docker 是一个在隔离容器中运行应用程序的工具。如果还没有安装，请访问 [docker.com](https://www.docker.com/) 按照指引安装。

## 分步安装

### 1. 下载 Nexent

```bash
git clone https://github.com/ModelEngine-Group/nexent.git
```

### 2. 进入 Docker 目录

```bash
cd nexent/docker
```

### 3. 创建配置文件

```bash
cp .env.example .env
```

用文本编辑器打开 `.env` 文件。基本设置只需填写语音服务凭据（如果不需要语音功能可以留空）。

### 4. 启动 Nexent

```bash
bash deploy.sh
```

脚本会下载并启动所有必要的容器。首次运行可能需要几分钟。

### 5. 打开浏览器

访问 **http://localhost:3000**，你会看到 Nexent 设置向导。

## 设置向导

首次打开 Nexent 时，向导会引导你完成：

1. **选择语言** — 英语或中文。
2. **连接 AI 模型** — 需要模型提供商的 API 密钥（如 OpenAI、SiliconFlow 等）。
3. **基本设置** — 命名工作空间并设置默认值。

## 停止和重启

停止 Nexent：

```bash
cd nexent/docker
docker compose down
```

重新启动：

```bash
bash deploy.sh
```

数据在重启之间会保留。

## 常见问题

| 问题 | 解决方案 |
|------|---------|
| 端口 3000 被占用 | 停止占用该端口的应用，或修改 `docker-compose.yml` 更换端口 |
| 内存不足 | 关闭其他程序，或在 Docker Desktop 设置中增加内存限制 |
| 容器启动失败 | 运行 `docker compose logs` 查看错误信息 |

准备好进行第一次对话了！
