---
title: "MCP集成"
weight: 3
bookToc: true
---

# MCP集成

## 简介

MCP（模型上下文协议）将LLM连接到外部服务。`mcp-builder`技能帮助创建MCP服务器。

## Skills + MCP

| Skills | MCP |
|--------|-----|
| 指令和流程 | 服务连接 |
| 文本规则 | 编程接口 |
| 静态知识 | 动态数据 |

## mcp-builder技能

```
mcp-builder/
├── SKILL.md
└── reference/
    ├── evaluation.md
    ├── python_mcp_server.md
    └── mcp_best_practices.md
```

支持Python（FastMCP）和TypeScript（MCP SDK）创建MCP服务器。

## 组合使用

技能可以指示Claude使用MCP工具：

```markdown
---
name: database-reporter
description: Creates database reports using MCP database tools
---

# 流程
1. 使用MCP工具`query_db`连接数据库
2. 执行分析查询
3. 将结果格式化为markdown表格
```

## 总结

- MCP将LLM连接到外部服务
- `mcp-builder`帮助创建MCP服务器
- Skills和MCP相互补充
