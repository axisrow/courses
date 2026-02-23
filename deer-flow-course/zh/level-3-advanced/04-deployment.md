---
title: "部署DeerFlow"
weight: 4
bookToc: true
---

# 部署DeerFlow

## 简介

在本课中，我们将介绍如何在生产环境中部署DeerFlow——从Docker Compose到Kubernetes。

## Docker Compose（推荐）

### 部署架构

```
Docker Compose
  ├─ nginx（端口2026）     ← 反向代理
  ├─ web（端口3000）       ← 前端
  ├─ api（端口8001）       ← Gateway API
  └─ langgraph（端口2024） ← LangGraph Server
```

### 步骤

#### 1. 准备服务器

```bash
sudo apt update
sudo apt install -y docker.io docker-compose-v2 git
sudo systemctl enable docker
```

#### 2. 克隆并配置

```bash
git clone https://github.com/bytedance/deer-flow.git
cd deer-flow
make config
```

#### 3. 设置环境变量

```bash
# .env
OPENAI_API_KEY=sk-your-key
```

#### 4. 配置沙箱

生产环境使用Docker沙箱：

```yaml
sandbox:
  use: src.community.aio_sandbox:AioSandboxProvider
```

#### 5. 初始化并启动

```bash
make docker-init    # 首次
make docker-start   # 启动
```

#### 6. 验证

```bash
curl http://localhost:2026/api/health
# 预期响应：{"status": "ok"}
```

## Kubernetes

用于可扩展的部署，每个沙箱运行在独立的pod中。

## 安全检查清单

- [ ] 使用Docker沙箱（非本地）
- [ ] API密钥仅通过环境变量设置
- [ ] 外部访问使用HTTPS
- [ ] 代理前设置身份验证
- [ ] 限制沙箱网络访问
- [ ] 定期更新Docker镜像

## 监控

```bash
make docker-logs              # 所有服务
docker compose logs -f api    # 特定服务
```

## 总结

- Docker Compose是推荐的部署方式
- 生产环境使用Docker沙箱
- 外部访问需配置HTTPS和身份验证
- API密钥——仅通过环境变量
- Kubernetes用于可扩展的部署
