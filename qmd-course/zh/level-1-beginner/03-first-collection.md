---
title: "你的第一个集合"
weight: 3
bookToc: true
---

# 你的第一个集合

## 什么是集合？

**集合**就是一个包含 markdown 文件的文件夹，QMD 会在其中搜索。你可以为不同内容创建不同的集合：

- 个人笔记
- 工作文档
- 会议记录
- 项目文档

## 添加集合

假设你的笔记在 `~/notes`：

```sh
qmd collection add ~/notes --name notes
```

完成！QMD 会扫描文件夹并索引所有 markdown 文件。

## 添加更多集合

```sh
qmd collection add ~/Documents/meetings --name meetings
qmd collection add ~/work/docs --name docs
```

## 自定义文件模式

```sh
qmd collection add ~/docs --name docs --mask "**/*.md"
```

## 列出集合

```sh
qmd collection list
```

## 删除集合

```sh
qmd collection remove notes
```

这只会从 QMD 索引中删除——你的文件不会受到影响。

## 重命名集合

```sh
qmd collection rename notes my-notes
```

## 浏览集合文件

```sh
qmd ls notes
qmd ls notes/subfolder
```

## 更新索引

添加或修改文件后：

```sh
qmd update
```

## 练习

1. 创建一个包含几个 markdown 文件的文件夹
2. 将其添加为集合
3. 运行 `qmd collection list` 验证
4. 运行 `qmd ls <集合名>` 查看文件

## 下一步

文档已索引！让我们学习如何搜索。
