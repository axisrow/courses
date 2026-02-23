---
title: "vLLM Pods"
weight: 2
bookToc: true
---

# vLLM Pods

## Introduction

The **pi-pods** package lets you deploy and manage LLMs on remote GPU servers with automatic vLLM configuration.

## What pi-pods Does

- Sets up vLLM on fresh Ubuntu servers
- Configures tool calling for agentic models
- Manages multiple models on one server
- Provides OpenAI-compatible API endpoints

## Installation

```bash
npm install -g @mariozechner/pi
```

## Requirements

- HuggingFace token
- GPU server with Ubuntu, SSH access, and NVIDIA drivers

## Supported Providers

- **DataCrunch** — NFS for shared model storage
- **RunPod** — persistent storage
- **Vast.ai**, **AWS EC2**, and any Ubuntu server with GPUs

## Quick Start

```bash
export HF_TOKEN=your_token
export PI_API_KEY=your_key

# Setup pod
pi pods setup dc1 "ssh root@1.2.3.4" \
  --mount "sudo mount -t nfs nfs.server:/path /mnt/hf-models"

# Start a model
pi start Qwen/Qwen2.5-Coder-32B-Instruct --name qwen

# Interactive chat
pi agent qwen -i
```

## Summary

- pi-pods automates LLM deployment on GPUs
- Supports DataCrunch, RunPod, and other providers
- Provides an OpenAI-compatible API
