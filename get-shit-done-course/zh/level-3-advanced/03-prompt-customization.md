---
title: "提示词定制"
level: 3
lesson: 3
language: zh
tags: [gsd, 定制, 提示词]
---

# 提示词定制

## 介绍

GSD 将斜杠命令安装为 markdown 文件。你可以研究并定制它们。

## 操作指南

### 命令位置

```
# 全局安装
~/.claude/commands/gsd/

# 本地安装
./.claude/commands/gsd/
```

每个命令是一个包含 Claude 指令的 markdown 文件。

### 通过 CONTEXT.md 定制

最简单的定制方式——通过 `/gsd:discuss-phase`。你的决策写入 CONTEXT.md 并影响所有后续步骤。

### 通过设置定制

```
/gsd:settings
```

控制启用哪些代理、模型配置文件、规划深度和 git 策略。

### 直接编辑命令

高级用户可以编辑 markdown 命令文件：

1. 打开 `~/.claude/commands/gsd/` 中的命令文件
2. 研究提示词结构
3. 添加或修改指令
4. 重启 Claude Code

> **警告：** GSD 更新会覆盖你的更改。请做备份。

### 本地覆盖

使用本地安装进行项目特定的定制：

```bash
npx get-shit-done-cc --claude --local
# 现在编辑 ./.claude/commands/gsd/
```

本地命令优先于全局命令。

## 示例

```bash
# 查看命令结构
ls ~/.claude/commands/gsd/

# 复制用于定制
cp -r ~/.claude/commands/gsd/ ./.claude/commands/gsd/
```

## 总结

- GSD 命令是 markdown 文件
- 通过 CONTEXT.md 定制是最简单的方式
- 可以直接编辑命令文件
- 本地命令覆盖全局命令
- GSD 更新会覆盖定制
