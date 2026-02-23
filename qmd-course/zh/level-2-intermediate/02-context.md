---
title: "添加上下文"
weight: 7
bookToc: true
---

# 为集合添加上下文

## 为什么上下文很重要？

上下文是 QMD 最强大的功能之一。当你为集合或文件夹添加描述时，该描述会随搜索结果一起返回。这帮助 AI 理解它看到的是*什么类型*的内容。

没有上下文：`notes/meeting.md — Score: 85%`

有上下文：`notes/meeting.md — Context: "每周团队站会笔记" — Score: 85%`

## 为集合添加上下文

```sh
qmd context add qmd://notes "个人笔记和想法"
qmd context add qmd://meetings "会议记录和笔记"
qmd context add qmd://docs "工作文档"
```

## 为子文件夹添加上下文

上下文以树状结构工作：

```sh
qmd context add qmd://docs/api "API 文档"
qmd context add qmd://notes/work "工作相关笔记"
```

## 从当前文件夹添加

```sh
cd ~/notes
qmd context add "个人笔记和想法"
```

## 全局上下文

```sh
qmd context add / "我的项目知识库"
```

## 查看和删除

```sh
qmd context list
qmd context rm qmd://notes/old
```

## 最佳实践

1. **描述要详细** — "2024年工程团队每周站会笔记"比"会议"好
2. **使用层次结构** — 集合设通用上下文，子文件夹设具体上下文
3. **为 AI 着想** — AI 需要知道什么才能理解这些文档？
4. **保持简洁** — 一个清晰的句子通常就够了

## 下一步

了解嵌入向量以及 QMD 如何理解文档的含义。
