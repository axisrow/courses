---
title: "系统技能（.system）"
weight: 4
bookToc: true
---

# 系统技能（.system）

## 简介

系统技能是内置于Codex的技能，安装后立即可用。它们位于`.system`文件夹中，不需要单独安装。

## 现有系统技能

目前Codex内置两个系统技能：

### 1. skill-installer

**功能：** 从openai/skills仓库或任何GitHub仓库安装新技能到Codex。

**使用场景：**
- 查看可用技能
- 安装精选或实验性技能
- 从第三方仓库安装技能

**示例：**

```
$skill-installer 显示可用技能
```

```
$skill-installer install gh-fix-ci
```

### 2. skill-creator

**功能：** 帮助创建新技能，引导您完成从构思到完成的整个过程。

**使用场景：**
- 创建自定义技能
- 更新现有技能

**示例：**

```
$skill-creator 创建一个数据库操作技能
```

## skill-installer结构

```
skill-installer/
├── SKILL.md
├── agents/openai.yaml
├── scripts/
│   ├── list-skills.py
│   ├── install-skill-from-github.py
│   └── github_utils.py
└── LICENSE.txt
```

## skill-creator结构

```
skill-creator/
├── SKILL.md
├── agents/openai.yaml
├── scripts/
│   ├── init_skill.py
│   ├── generate_openai_yaml.py
│   └── quick_validate.py
└── references/
    └── openai_yaml.md
```

## 总结

- Codex内置两个系统技能：skill-installer和skill-creator
- skill-installer从GitHub安装技能
- skill-creator帮助创建自己的技能
- 系统技能无需安装，开箱即用
