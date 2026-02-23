---
title: "架构深入解析"
weight: 1
bookToc: true
---

# 架构深入解析

## 系统概览

PageIndex 由几个相互关联的组件组成，它们协同工作，将原始文档转换为可搜索的树结构。

## 核心模块

### page_index.py — 主引擎

这是 PageIndex 的核心，包含以下逻辑：

- **目录检测**（`find_toc_pages`、`toc_detector_single_page`）：扫描页面查找目录
- **目录提取**（`toc_extractor`、`extract_toc_content`）：提取和清理目录内容
- **目录转换**（`toc_transformer`）：将原始目录文本转为结构化 JSON
- **页码映射**（`toc_index_extractor`、`calculate_page_offset`）：将逻辑页码映射到物理 PDF 页码
- **验证**（`verify_toc`、`check_title_appearance`）：验证生成树的准确性
- **错误修正**（`fix_incorrect_toc`、`fix_incorrect_toc_with_retries`）：修复错误的页码分配
- **递归分解**（`process_large_node_recursively`）：将大章节拆分为子章节

### utils.py — 工具函数

提供辅助功能：
- OpenAI API 通信（同步和异步）
- Token 计数
- JSON 提取和解析
- 树结构后处理
- PDF 文本提取

### config.yaml — 默认配置

```yaml
model: "gpt-4o-2024-11-20"
toc_check_page_num: 20
max_page_num_each_node: 10
max_token_num_each_node: 20000
if_add_node_id: "yes"
if_add_node_summary: "yes"
if_add_doc_description: "no"
if_add_node_text: "no"
```

## 处理流水线

```
PDF 输入
  │
  ▼
提取页面文本和 token 计数
  │
  ▼
检测目录（扫描前 N 页）
  │
  ├─ 带页码的目录 → 提取、映射偏移量、验证
  ├─ 不带页码的目录 → 提取、扫描页码、验证
  └─ 没有目录 → 从全文生成结构
  │
  ▼
验证准确性（检查标题↔页码匹配）
  │
  ├─ 准确率 ≥ 60% → 修复错误条目
  └─ 准确率 < 60% → 回退到下一策略
  │
  ▼
递归分解大节点
  │
  ▼
添加节点 ID、摘要、描述
  │
  ▼
输出 JSON 树
```

## 并发模型

PageIndex 使用 Python 的 `asyncio` 和 `asyncio.gather` 进行并发处理，显著加速大文档的处理。

## 元处理器模式

`meta_processor` 函数实现了带自动回退的策略模式：

1. 先尝试信息最丰富的策略（带页码的目录）
2. 如果准确率低于阈值，回退到下一策略
3. 继续回退直到某个策略成功

这使 PageIndex 能够可靠地处理各种质量的文档。

## 总结

PageIndex 的架构是一个包含检测、提取、映射、验证和修正的流水线——配合智能回退和并发处理。理解这些组件有助于自定义和扩展系统。
