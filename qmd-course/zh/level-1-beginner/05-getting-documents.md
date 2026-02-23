---
title: "获取文档"
weight: 5
bookToc: true
---

# 获取文档

## 获取单个文档

```sh
qmd get "notes/meeting-2024-01-15.md"
```

## 使用文档 ID

搜索结果中的短 ID（如 `#a1b2c3`）可直接使用：

```sh
qmd get "#a1b2c3"
```

## 从特定行开始

```sh
qmd get "notes/meeting.md:50"
```

## 限制输出行数

```sh
qmd get notes/meeting.md -l 100
qmd get notes/meeting.md:50 -l 100
```

## 获取多个文档

```sh
# 通配符模式
qmd multi-get "journals/2025-05*.md"

# 逗号分隔列表
qmd multi-get "doc1.md, doc2.md, #abc123"
```

## 搜索结果中显示完整内容

```sh
qmd search "API" --full
```

## 添加行号

```sh
qmd get notes/meeting.md --line-numbers
```

## 导出所有匹配文件

```sh
qmd search "API" --all --files --min-score 0.3
```

## 练习

1. 从搜索结果中记下一个文档 ID
2. 用 `qmd get "#<id>"` 获取该文档
3. 用 `qmd multi-get` 尝试通配符模式

## 初级阶段总结

恭喜完成初级阶段！你现在能够：

- ✅ 安装和配置 QMD
- ✅ 创建和管理集合
- ✅ 使用关键词、语义和混合搜索
- ✅ 通过路径、ID 或模式获取文档

**下一阶段**：输出格式、上下文、嵌入向量和高级搜索技巧。
