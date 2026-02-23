---
title: "Supabase 数据库"
weight: 7
bookToc: true
---

# Supabase 数据库

为应用存储和获取数据。

## 什么是 Supabase？

Supabase 是一个开源后端：PostgreSQL 数据库、认证和 API。Lovable 原生集成 Supabase。

## 连接 Supabase

1. 在项目设置中点击 **Supabase**。
2. Lovable 可以自动为你创建 Supabase 项目。
3. 或用你的项目 URL 和 anon key 连接现有项目。

## 创建表

> 创建 "posts" 表，包含列：id、title、content、created_at。在首页显示所有文章。

Lovable 会：
- 在 Supabase 中创建表。
- 生成获取和显示数据的代码。
- 添加 TypeScript 类型。

## CRUD 操作

> 用户可以通过表单创建文章。每篇文章添加编辑和删除按钮。

完整的增删改查就绪。

## 实时数据

> 当有新文章添加时，文章列表实时更新。

## 行级安全（RLS）

> 用户只能编辑自己的文章。

AI 会设置正确的 RLS 策略。

## 常见数据库模式

| 模式 | 示例 |
|------|------|
| 用户资料 | 姓名、头像、简介 |
| 内容管理 | 文章、评论 |
| 电商 | 商品、订单、购物车 |
| 分析 | 事件、浏览量、指标 |

## 总结

Supabase 为 Lovable 应用提供强大的数据库。通过提示词创建表、执行 CRUD、使用实时更新和数据安全。
