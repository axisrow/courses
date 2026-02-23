---
title: "创建简单技能"
weight: 4
bookToc: true
---

# 创建简单技能

## 简介

在本课中，我们将从头创建第一个技能。

## 第1步：构思创意

好的技能解决特定的重复性任务。示例：
- 按公司模板格式化报告
- 按团队标准检查代码
- 以特定风格生成文档

本课我们将创建一个**greeting**技能——用不同语言问候用户。

## 第2步：初始化技能

使用skill-creator中的`init_skill.py`：

```bash
python scripts/init_skill.py greeting --path ./skills
```

创建的结构：

```
skills/greeting/
├── SKILL.md
└── agents/
    └── openai.yaml
```

## 第3步：编写SKILL.md

```markdown
---
name: greeting
description: 用不同语言问候用户。当用户要求问候某人、创建欢迎消息或翻译问候语时使用。
---

# Greeting

用不同语言创建问候。

## 支持的语言

- English: "Hello, {name}! Welcome!"
- 中文: "{name}，你好！欢迎！"
- Русский: «Привет, {name}! Добро пожаловать!»
- Español: "¡Hola, {name}! ¡Bienvenido!"

## 指令

1. 从上下文确定目标语言
2. 将用户名插入模板
3. 如未指定语言，默认使用英语
```

## 第4步：配置openai.yaml

```yaml
display_name: "Greeting"
short_description: "多语言问候"
default_prompt: "问候用户"
```

## 第5步：验证

```bash
python scripts/quick_validate.py ./skills/greeting
```

## 第6步：安装

```bash
cp -r ./skills/greeting ~/.codex/skills/
```

重启Codex——技能就绪！

## 总结

- 技能创建从`init_skill.py`开始
- 主文件是带有frontmatter和指令的SKILL.md
- `openai.yaml`提供UI元数据
- `quick_validate.py`检查错误
- 复制到`~/.codex/skills/`即可使用
