---
title: "解读和使用结果"
weight: 5
bookToc: true
---

# 解读和使用结果

## 理解输出

当 PageIndex 处理完一个文档后，会生成一个 JSON 文件。让我们学习如何解读和使用这个输出。

## 输出结构

一个完整的 PageIndex 输出如下：

```json
{
  "doc_name": "2023-annual-report",
  "structure": [
    {
      "title": "致股东信",
      "node_id": "0001",
      "start_index": 1,
      "end_index": 3,
      "summary": "CEO 讨论了主要成就和战略..."
    },
    {
      "title": "财务概览",
      "node_id": "0002",
      "start_index": 4,
      "end_index": 50,
      "summary": "2023 财年的综合财务业绩",
      "nodes": [
        {
          "title": "收入分析",
          "node_id": "0003",
          "start_index": 4,
          "end_index": 15,
          "summary": "按业务板块和地区的详细收入明细"
        }
      ]
    }
  ]
}
```

## 关键字段说明

### 页码索引
- **start_index**：该章节的起始页（从 1 开始）
- **end_index**：该章节的结束页

这让您可以从原始 PDF 中精确提取对应的页面。

### 节点 ID
每个章节都有一个唯一的 **node_id**（如 "0001"、"0002"），用于：
- 在应用中引用特定章节
- 构建章节之间的关联
- 追踪哪些章节被用来回答了问题

### 摘要
**summary** 字段提供每个章节内容的简洁描述。摘要由大语言模型生成，对树搜索至关重要。

### 嵌套节点
**nodes** 数组包含子章节，形成层级关系：
- 没有 `nodes` 的章节是叶子节点（最具体的层级）
- 有 `nodes` 的章节是分支，包含子章节

## 实用技巧

### 技巧一：用代码遍历树

```python
import json

with open("results/document_structure.json") as f:
    data = json.load(f)

def print_tree(nodes, indent=0):
    for node in nodes:
        pages = f"(第 {node['start_index']}-{node['end_index']} 页)"
        print("  " * indent + f"- {node['title']} {pages}")
        if "nodes" in node:
            print_tree(node["nodes"], indent + 1)

print_tree(data["structure"])
```

### 技巧二：按主题查找章节

```python
def find_sections(nodes, keyword):
    results = []
    for node in nodes:
        if keyword.lower() in node.get("summary", "").lower():
            results.append(node)
        if "nodes" in node:
            results.extend(find_sections(node["nodes"], keyword))
    return results
```

### 技巧三：提取章节对应的页面

知道 `start_index` 和 `end_index` 后，可以使用任何 PDF 库从原始文档中提取这些页面。

## 总结

PageIndex 的输出是一个结构化的 JSON 树，包含标题、页码范围、ID 和摘要。理解这个格式可以让您在 PageIndex 的基础上构建强大的应用——从文档搜索到自动化报告分析。
