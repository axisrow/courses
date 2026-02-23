---
title: "使用代码库"
level: 2
lesson: 4
lang: zh
tags: [代码, 会话, 分支, 上下文]
---

# 使用代码库

## 介绍

OMP 擅长导航和编辑大型项目。

## 文件引用

```
> 解释 @src/auth/middleware.ts
> 比较 @old.ts 和 @new.ts
```

支持 @ + Tab 自动补全，遵循 `.gitignore`。

## Bash 模式

```
> !git log --oneline -10
> !find src -name "*.test.ts" | head -20
```

`!!` — 执行但不添加到模型上下文。

## 会话管理

会话以 JSONL 格式存储在 `~/.omp/agent/sessions/`。

```bash
omp -c                    # 继续上次
omp -r                    # 从列表选择
omp -r abc123             # 按 ID 前缀
omp --no-session          # 不保存
```

## 会话分支

- `/tree` — 导航会话树
- `/branch` — 从过去的消息创建分支
- `/fork` — 分叉会话

## 上下文压缩

```
/compact                    # 手动压缩
/compact 关注 API 部分       # 指定焦点
```

自动压缩可在设置中配置。

## 规划模式

```
/plan
> 规划从 PostgreSQL 到 SQLite 的数据库迁移
```

## 代码审查

```
/review
```

交互选择：分支比较、未提交更改、提交审查。

## 总结

OMP 为大型项目提供了完整的导航、编辑和会话管理工具集。
