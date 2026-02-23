---
title: "扩展和贡献 RAPTOR"
weight: 5
bookToc: true
---

## 扩展和贡献 RAPTOR

### RAPTOR 专为扩展而设计

模块化架构使添加新功能变得简单。

### 添加新包

1. 在 `packages/` 中创建新目录:

```
packages/your_capability/
  ├── __init__.py
  ├── analyzer.py
  └── config.py
```

2. 在 `raptor.py` 中注册
3. 在 `.claude/commands/your-command.md` 中创建 Claude 命令

### 创建自定义技能

`/create-skill` 命令让你保存自定义方法:

```
/create-skill
```

技能存储在 `.claude/skills/` 中，在未来的会话中自动可用。

### 专家角色

你可以通过向 Tier 2 系统添加 markdown 文件来创建新的专家角色。角色定义:

- **身份** — 专家是谁
- **方法** — 如何分析问题
- **专注领域** — 专业方向
- **沟通风格** — 如何呈现发现

### 为社区做贡献

RAPTOR 是开源的（MIT 许可证），欢迎贡献:

- 新的 Semgrep 规则
- 针对特定语言的 CodeQL 查询
- 流行库的模糊测试工具
- 新 AI 提供商的集成
- 文档改进和翻译

### 社区

- **GitHub Issues**:https://github.com/gadievron/raptor/issues
- **Slack**:Prompt||GTFO 的 #raptor 频道

### 贡献者的想法

- YARA 签名生成
- 移植到其他 AI 编程助手（Cursor、Windsurf、Copilot、Codex）
- 更好的 Web 利用模块
- 与漏洞赏金平台集成

### 核心要点

RAPTOR 的力量来自社区。无论你是编写规则、改进工具还是分享知识，你的贡献都让安全研究对每个人来说变得更好。
