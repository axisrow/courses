---
title: "创建自定义 MCP 服务器"
weight: 11
bookToc: true
---

# 创建自定义 MCP 服务器

## 为什么要自己创建？

Sentient 附带 20+ 集成，但你可能需要连接尚不支持的服务——公司内部 API、小众 SaaS 工具或智能家居系统。

## MCP 服务器结构

`src/server/mcp_hub/` 中每个 MCP 服务器都遵循相同的模式：

```
my_service/
├── main.py        # 工具定义和处理程序
├── auth.py        # 认证逻辑
├── utils.py       # 辅助函数
├── prompts.py     # AI 使用的系统提示词
└── test_client.py # 测试
```

## 分步创建

### 1. 创建文件夹

```bash
mkdir src/server/mcp_hub/my_service
```

### 2. 在 `main.py` 中定义工具

```python
async def get_items(query: str) -> dict:
    """在 My Service 中搜索项目。"""
    response = await client.get(f"/api/items?q={query}")
    return response.json()
```

### 3. 在 `auth.py` 中处理认证

OAuth 可参考 `gmail/auth.py`。简单 API 密钥可存在 `.env` 中。

### 4. 编写 `prompts.py`

```python
SYSTEM_PROMPT = """
当用户询问库存、产品可用性或订单状态时，
使用 my_service 工具。
"""
```

### 5. 注册 MCP 服务器

将新服务器添加到编排器配置中。

### 6. 测试

使用 `test_client.py` 验证工具正常工作。

## 最佳实践

- 一个工具做一件事。
- 返回结构化数据（JSON）。
- 优雅处理错误。
- 编写清晰的工具描述。

## 小结

掌握模式后，创建一个 MCP 服务器大约需要一小时。这是扩展 Sentient 最强大的方式。
