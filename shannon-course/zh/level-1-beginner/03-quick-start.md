---
title: "快速入门"
weight: 3
bookToc: true
---

# 快速入门

## 简介

一切安装就绪后，让我们启动Shannon并学习基本命令。

## 准备仓库

Shannon分析应用程序的源代码。将其放入`./repos/`目录：

```bash
git clone https://github.com/your-org/your-app.git ./repos/your-app
```

多仓库应用（前端+后端）：

```bash
mkdir ./repos/my-app
cd ./repos/my-app
git clone https://github.com/your-org/frontend.git
git clone https://github.com/your-org/backend.git
```

## 运行渗透测试

一条命令启动：

```bash
./shannon start URL=https://your-app.com REPO=your-app
```

- `URL` — 运行中应用的地址
- `REPO` — `./repos/`中的文件夹名

## 监控进度

```bash
./shannon logs                          # 实时日志
./shannon query ID=shannon-1234567890   # 查询特定workflow
open http://localhost:8233              # Temporal Web UI
```

## 停止Shannon

```bash
./shannon stop              # 停止容器（保留数据）
./shannon stop CLEAN=true   # 完全清理
```

## 测试本地应用

Docker容器无法访问主机的`localhost`，使用：

```bash
./shannon start URL=http://host.docker.internal:3000 REPO=my-app
```

## 总结

- 学会了准备分析仓库
- 掌握了主命令`./shannon start`
- 可以通过日志和Web UI跟踪进度
- 知道如何测试本地应用
