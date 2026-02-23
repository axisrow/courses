---
title: "发布技能"
weight: 4
bookToc: true
---

# 发布技能

## 简介

您已创建并测试了技能——现在是分享它的时候了。

## 方法1：GitHub仓库

最简单的方式——在您自己的GitHub仓库中发布技能。

### 第1步：创建仓库

```bash
mkdir my-skills && cd my-skills
git init
```

### 第2步：添加技能

```
my-skills/
└── csv-analyzer/
    ├── SKILL.md
    ├── agents/openai.yaml
    ├── scripts/analyze.py
    └── LICENSE.txt
```

### 第3步：发布

```bash
git add .
git commit -m "Add csv-analyzer skill"
git remote add origin https://github.com/you/my-skills.git
git push -u origin main
```

### 第4步：其他人可以安装

```
$skill-installer install https://github.com/you/my-skills/tree/main/csv-analyzer
```

## 方法2：为openai/skills做贡献

您可以将技能提交到官方仓库。详见下一课。

## 许可证

每个技能都应包含`LICENSE.txt`文件。

## 发布前检查清单

- [ ] 技能通过验证
- [ ] 所有脚本已测试
- [ ] SKILL.md有清晰的描述
- [ ] `agents/openai.yaml`已填写
- [ ] 包含`LICENSE.txt`
- [ ] 没有敏感数据（密钥、密码、令牌）

## 总结

- 通过GitHub仓库发布技能
- Skill-installer可以从任何GitHub仓库安装
- 每个技能都要包含许可证
- 发布前检查敏感数据
