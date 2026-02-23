---
title: "深入了解Skill-installer"
weight: 2
bookToc: true
---

# 深入了解Skill-installer

## 简介

Skill-installer是Codex的内置系统技能，管理其他技能的安装。

## 主要命令

### 列出可用技能

```
$skill-installer
```

### 按名称安装精选技能

```
$skill-installer gh-address-comments
```

### 从其他文件夹安装

```
$skill-installer install the create-plan skill from the .experimental folder
```

### 从任何GitHub仓库安装

```
$skill-installer install https://github.com/user/repo/tree/main/my-skill
```

## 安装过程

1. Skill-installer从GitHub下载技能文件夹
2. 复制到`~/.codex/skills/技能名/`
3. 如果已安装则中止
4. 安装后需要重启Codex

## 私有仓库

- 使用现有git凭据
- 可设置`GITHUB_TOKEN`或`GH_TOKEN`
- 先尝试HTTPS，然后SSH

## 总结

- Skill-installer是安装技能的通用工具
- 支持精选、实验性和第三方技能
- 支持私有仓库
- 安装后务必重启Codex
