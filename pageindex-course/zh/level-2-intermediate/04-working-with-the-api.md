---
title: "使用 API 与集成"
weight: 4
bookToc: true
---

# 使用 API 与集成

## PageIndex 的使用方式

除了在本地运行，还有多种方式将 PageIndex 集成到您的工作流中：

1. **Python API** — 直接在代码中调用 PageIndex 函数
2. **云端 API** — 通过 HTTP 请求使用托管服务
3. **MCP** — 将 PageIndex 连接到 Claude 或 Cursor 等 AI 助手
4. **聊天平台** — 使用 Web 界面进行交互式文档分析

## 使用 Python API

最简单的编程方式：

```python
from pageindex import page_index

result = page_index(
    "path/to/document.pdf",
    model="gpt-4o-2024-11-20",
    if_add_node_summary="yes",
    if_add_node_id="yes"
)
```

`result` 字典包含：
- `doc_name` — 文档名称
- `structure` — 完整的树结构，包含章节、页码范围和摘要
- `doc_description` — （可选）整个文档的描述

## 配置选项

可以通过参数自定义行为：

```python
result = page_index(
    "document.pdf",
    model="gpt-4o-2024-11-20",
    toc_check_page_num=20,        # 扫描目录的页数
    max_page_num_each_node=10,     # 每个节点最大页数
    max_token_num_each_node=20000, # 每个节点最大 token 数
    if_add_node_summary="yes",     # 生成章节摘要
    if_add_doc_description="yes",  # 生成文档描述
    if_add_node_text="no"          # 在节点中包含原始文本
)
```

## 构建简单的 RAG 流水线

Cookbook 中包含一个完整的无向量 RAG 系统示例：

1. **生成树** — 用 PageIndex 处理文档
2. **接收问题** — 获取用户查询
3. **搜索树** — 用大语言模型在树结构中推理
4. **提取相关页面** — 从定位到的章节获取内容
5. **生成回答** — 用大语言模型基于提取的内容回答

整个流水线不需要任何向量数据库或分块。

## 视觉 RAG

PageIndex 还支持基于视觉的方式——直接使用**页面图片**而不是提取文本。这对于有复杂布局、图表或表格的文档特别有用。

## MCP 集成

MCP（模型上下文协议）允许 AI 助手将 PageIndex 作为工具使用。配置好后，您可以在工作流中让 Claude 或 Cursor 直接使用 PageIndex 的能力来分析文档。

## 总结

PageIndex 提供多种集成路径：Python API 直接调用、云服务、面向 AI 助手的 MCP，以及交互式聊天平台。每种方式都能访问同样强大的基于树的推理检索。
