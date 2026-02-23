---
title: "使用数据库"
weight: 12
bookToc: true
---

# 使用数据库

## 什么是数据库？

数据库存储应用的信息：用户账号、博客文章、产品列表、订单等。

把它想象成一个智能电子表格，你的应用可以自动读写。

## v0 中的数据库

v0 内置数据库连接支持：

- 创建数据结构（schema）
- 生成读写数据的代码
- 自动设置连接

## 如何添加数据库

1. 在提示词中描述你需要什么数据：
   - "Create a to-do app that saves tasks to a database"
   - "Build a blog with posts stored in a database"
2. v0 会建议或设置数据库（通常是 Supabase 或 Vercel Postgres）
3. 按指示创建数据库账号

## 基本操作

| 操作 | 作用 | 示例 |
|------|------|------|
| Create | 添加新数据 | 发布新博客文章 |
| Read | 读取已有数据 | 显示所有产品 |
| Update | 修改已有数据 | 编辑用户资料 |
| Delete | 删除数据 | 删除评论 |

这些叫做 **CRUD** 操作。

## 数据库提供商

- **Vercel Postgres** — Vercel 生态内置
- **Supabase** — 流行，免费额度大
- **PlanetScale** — 基于 MySQL
- **Neon** — 无服务器 Postgres

## 技巧

- 从简单的数据结构开始
- 在构建前想好应用需要什么数据
- 用 AI 帮你设计数据库结构

## 总结

数据库存储应用数据。v0 可以设置连接并生成所有需要的代码。下一课——智能代理功能。
