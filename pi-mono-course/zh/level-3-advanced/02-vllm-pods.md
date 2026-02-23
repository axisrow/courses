---
title: "vLLM Pods"
weight: 2
bookToc: true
---

# vLLM Pods

## 简介

**pi-pods** 包允许你在远程 GPU 服务器上部署和管理 LLM，并自动配置 vLLM。

## pi-pods 的功能

- 在全新的 Ubuntu 服务器上设置 vLLM
- 为代理模型配置工具调用
- 在一台服务器上管理多个模型
- 提供 OpenAI 兼容的 API 端点

## 安装

```bash
npm install -g @mariozechner/pi
```

## 要求

- HuggingFace 令牌
- 带有 Ubuntu、SSH 访问和 NVIDIA 驱动的 GPU 服务器

## 支持的提供商

- **DataCrunch** — NFS 共享模型存储
- **RunPod** — 持久存储
- **Vast.ai**、**AWS EC2** 及任何带 GPU 的 Ubuntu 服务器

## 快速开始

```bash
export HF_TOKEN=你的令牌
export PI_API_KEY=你的密钥

# 设置 pod
pi pods setup dc1 "ssh root@1.2.3.4" \
  --mount "sudo mount -t nfs nfs.server:/path /mnt/hf-models"

# 启动模型
pi start Qwen/Qwen2.5-Coder-32B-Instruct --name qwen

# 交互式聊天
pi agent qwen -i
```

## 总结

- pi-pods 自动化 GPU 上的 LLM 部署
- 支持 DataCrunch、RunPod 和其他提供商
- 提供 OpenAI 兼容 API
