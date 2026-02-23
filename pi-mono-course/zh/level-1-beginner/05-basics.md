---
title: "工作基础"
weight: 5
bookToc: true
---

# 工作基础

## 简介

在本课中，我们将学习核心概念：会话、上下文文件和技能。

## 会话

Pi 将对话历史保存在会话中。你可以：

- 继续之前的对话
- 从任何点创建分支
- 压缩长历史以节省令牌

```bash
pi --session my-session    # 继续或创建会话
pi --sessions              # 列出会话
```

## 上下文文件

项目根目录中的 `AGENTS.md` 和 `TOOLS.md` 文件会自动加载到代理的上下文中：

```markdown
# AGENTS.md
这个项目是一个 React Web 应用。
使用 TypeScript 并遵循我们的代码风格。
```

## 技能（Skills）

技能是 Pi 在需要时加载的指令文件。创建 `.pi/skills/` 文件夹：

```bash
mkdir -p .pi/skills
echo "处理数据库时使用 Prisma ORM" > .pi/skills/database.md
```

## 扩展（Extensions）

扩展是为代理添加新工具的 TypeScript 模块。可以通过 npm 安装或自己编写。

## 快捷键

| 按键 | 操作 |
|------|------|
| `Ctrl+C` | 取消/退出 |
| `Shift+Ctrl+D` | 调试 |
| `Enter` | 发送消息 |

## 总结

- 会话存储对话历史
- AGENTS.md 和 TOOLS.md 设置项目上下文
- 技能和扩展允许你自定义代理
