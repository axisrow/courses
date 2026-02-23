---
title: "QMD 与 AI 代理"
weight: 9
bookToc: true
---

# 将 QMD 与 AI 代理配合使用

## 为什么要连接 AI？

像 Claude 这样的 AI 助手非常强大，但它们不了解*你的*文件。QMD 架起了桥梁——让 AI 工具能搜索你的个人知识库。

## 命令行集成

最简单的方法：让 AI 代理运行 QMD 命令：

```sh
qmd search "认证" --json -n 10
qmd query "错误处理" --all --files --min-score 0.4
qmd get "docs/api-reference.md" --full
```

## MCP 服务器

MCP（Model Context Protocol）是 AI 工具连接数据源的标准协议。

### 可用的 MCP 工具

| 工具 | 描述 |
|------|------|
| `qmd_search` | 快速关键词搜索 |
| `qmd_vector_search` | 语义向量搜索 |
| `qmd_deep_search` | 深度搜索（含查询扩展和重排序） |
| `qmd_get` | 通过路径或 ID 获取文档 |
| `qmd_multi_get` | 获取多个文档 |
| `qmd_status` | 索引状态信息 |

### Claude Desktop 配置

```json
{
  "mcpServers": {
    "qmd": {
      "command": "qmd",
      "args": ["mcp"]
    }
  }
}
```

### Claude Code 配置

```bash
claude marketplace add tobi/qmd
claude plugin add qmd@qmd
```

## 使用方式

连接后，你可以问 Claude：

- "搜索我的笔记中关于 Q4 预算的内容"
- "找到所有关于产品发布的会议记录"
- "我写过什么关于数据库迁移的内容？"

## 下一步

学习索引维护和保持 QMD 健康运行。
