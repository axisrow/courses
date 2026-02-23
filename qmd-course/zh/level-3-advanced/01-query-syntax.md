---
title: "高级查询语法"
weight: 11
bookToc: true
---

# 高级查询语法

## Query Markup Documents

QMD 有自己的查询语言。你可以编写带有不同搜索类型的结构化多行查询，而不是输入单个搜索字符串。

## 查询类型

| 类型 | 方法 | 描述 |
|------|------|------|
| `lex` | BM25 关键词 | 精确词语匹配 |
| `vec` | 向量语义 | 基于含义的相似性 |
| `hyde` | 假设文档 | 写出你期望答案的样子 |
| `expand` | LLM 驱动 | 自动生成 lex/vec/hyde 变体 |

## 默认行为

没有类型前缀的查询被视为 `expand:`：

```sh
# 这两种等价：
qmd query "认证如何工作"
qmd query "expand: 认证如何工作"
```

## Lex 查询语法

| 语法 | 含义 | 示例 |
|------|------|------|
| `词语` | 前缀匹配 | `perf` 匹配 "performance" |
| `"短语"` | 精确短语 | `"rate limiter"` |
| `-词语` | 排除 | `-sports` |
| `-"短语"` | 排除短语 | `-"test data"` |

```sh
qmd query 'lex: "machine learning" -"deep learning"'
```

## Vec 查询

用自然语言提问：

```sh
qmd query 'vec: 速率限制器如何处理突发流量'
```

## Hyde 查询

写一个假设性的答案（50-100 词）：

```sh
qmd query 'hyde: 速率限制器使用滑动窗口算法，窗口为60秒。当客户端每分钟超过100个请求时，后续请求返回429错误。'
```

## 多行查询

组合多种类型，第一个查询获得双倍权重：

```sh
qmd query $'lex: rate limiter algorithm\nvec: how does rate limiting work\nhyde: The API implements rate limiting using a token bucket...'
```

## 限制

- 每个查询最多一个 `expand:`
- Lex 操作符仅在 `lex` 查询中有效
- 空行被忽略

## 下一步

深入了解混合搜索和重排序的工作原理。
