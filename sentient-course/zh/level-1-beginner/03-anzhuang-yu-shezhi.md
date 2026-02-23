---
title: "安装与设置"
weight: 3
bookToc: true
---

# 安装与设置

## 前提条件

- 运行 **Windows、macOS 或 Linux** 的电脑。
- 已安装 **Docker**（推荐 Docker Desktop）。
- **Node.js** 18 以上版本（用于客户端）。
- **Python 3.11+**（用于服务器）。
- **Git**（用于克隆代码库）。

## 第一步 — 克隆代码库

```bash
git clone https://github.com/existence-master/Sentient.git
cd Sentient
```

## 第二步 — 配置环境变量

```bash
cp src/server/.env.template src/server/.env
cp src/client/.env.template src/client/.env
```

打开每个 `.env` 文件，填写所需的值（API 密钥、数据库地址等）。

## 第三步 — 启动数据库

```bash
docker compose -f start_pgvector.yaml up -d
docker compose -f start_redis.yaml up -d
docker compose -f start_chroma.yaml up -d
docker compose -f start_litellm.yaml up -d
```

## 第四步 — 启动服务器

```bash
cd src/server
pip install -r requirements.txt
python -m uvicorn main.app:app --reload
```

## 第五步 — 启动客户端

```bash
cd src/client
npm install
npm run dev
```

在浏览器中打开 `http://localhost:3000`。

## Docker Compose 一键部署

```bash
docker compose -f src/docker-compose.selfhost.yml up -d
```

## 小结

Sentient 已在本地运行。下一课你将进行第一次对话。
