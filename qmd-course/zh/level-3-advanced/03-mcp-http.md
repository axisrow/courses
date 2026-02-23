---
title: "MCP HTTP 服务器"
weight: 13
bookToc: true
---

# MCP HTTP 服务器

## Stdio 与 HTTP

默认情况下，QMD 的 MCP 服务器以子进程（stdio）方式运行。每个客户端启动自己的副本并重新加载模型。对于共享的常驻服务器，使用 HTTP 传输。

## 启动 HTTP 服务器

```sh
# 前台运行
qmd mcp --http                    # localhost:8181
qmd mcp --http --port 8080        # 自定义端口

# 后台守护进程
qmd mcp --http --daemon
```

## 停止

```sh
qmd mcp stop
```

## 检查状态

```sh
qmd status
# 显示 "MCP: running (PID ...)"
```

## HTTP 端点

| 端点 | 方法 | 描述 |
|------|------|------|
| `/mcp` | POST | MCP Streamable HTTP（JSON） |
| `/health` | GET | 健康检查 |

## 连接

将客户端指向：`http://localhost:8181/mcp`

## 性能优势

- AI 模型保持在 GPU 内存中
- 首次请求：约 1 秒
- 后续请求：几乎即时
- 空闲 5 分钟后释放上下文，下次请求时透明重建

## 何时使用

**HTTP**：多个代理、频繁查询、需要速度。

**Stdio**：单个客户端、简单优先。

## 安全说明

服务器仅监听 `localhost`。如需远程访问，请使用带认证的反向代理。

## 下一步

了解智能分块算法。
