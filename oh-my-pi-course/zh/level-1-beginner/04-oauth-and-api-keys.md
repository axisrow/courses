---
title: "OAuth 和 API 密钥"
level: 1
lesson: 4
lang: zh
tags: [api, oauth, 服务商, 认证]
---

# OAuth 和 API 密钥

## 介绍

OMP 需要访问 AI 服务商。有两种方式：环境变量和交互式 `/login`。

## 方式 1：环境变量

导出服务商的密钥：

```bash
# Anthropic (Claude)
export ANTHROPIC_API_KEY="sk-ant-..."

# OpenAI
export OPENAI_API_KEY="sk-..."

# Google Gemini
export GEMINI_API_KEY="..."

# xAI (Grok)
export XAI_API_KEY="..."

# OpenRouter（访问多种模型）
export OPENROUTER_API_KEY="..."
```

将配置添加到 `~/.bashrc` 或 `~/.zshrc` 以持久保存。

## 方式 2：交互式 /login

```bash
omp
/login
```

支持 OAuth 的服务商包括：Anthropic、ChatGPT、GitHub Copilot、Google Cloud、Cursor、Perplexity、Ollama 等。

## 凭证行为

- `/login` **追加**凭证（不会覆盖已有的）
- `/logout` 清除选定服务商的凭证
- 凭证存储在 `~/.omp/agent/agent.db`
- API 密钥优先于 OAuth

## 本地模型 (Ollama)

```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.1
omp
/login
# 选择 ollama
```

Ollama 的 API 密钥是可选的。

## 总结

通过环境变量或 `/login` 配置 API 密钥。可以同时使用多个服务商。
