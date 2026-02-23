---
title: "深入了解:静态分析"
weight: 1
bookToc: true
---

## 深入了解:静态分析

### 两个引擎，一个目标

RAPTOR 使用两个互补的静态分析引擎:

#### Semgrep

Semgrep 是一个模式匹配工具。它查找与已知漏洞模式匹配的代码。RAPTOR 自带规则位于 `engine/semgrep/rules/`:

- `sinks/ssrf.yaml` — 服务端请求伪造
- `injection/sql-concat.yaml` — 字符串拼接导致的 SQL 注入
- `injection/command-taint.yaml` — 命令注入
- `crypto/weak-hash.yaml` — 弱哈希算法（MD5、SHA1）
- `secrets/hardcoded-api-key.yaml` — 硬编码 API 密钥
- `auth/tls-skip-verify.yaml` — 禁用 TLS 验证

#### CodeQL

CodeQL 是 GitHub 的语义分析引擎。与 Semgrep 的模式匹配不同，CodeQL 理解**数据流**——它可以追踪不可信的用户输入如何通过程序流向危险函数。

### 何时使用哪个

| 特性 | Semgrep | CodeQL |
|------|---------|--------|
| 速度 | 非常快 | 较慢（需构建数据库）|
| 准确性 | 基于模式（更多误报）| 数据流感知（更少误报）|
| 设置 | 最少 | 需要创建数据库 |

### 单独运行 CodeQL

```
/codeql
```

### 数据流验证

RAPTOR 尝试通过追踪从**源**（用户输入）到**汇**（危险函数）的数据流来验证发现。经验证的发现更可能是真正的漏洞。

### 核心要点

使用 Semgrep 进行快速、广泛的扫描。使用 CodeQL 进行更少误报的深入分析。RAPTOR 将两者结合以获得最佳结果。
