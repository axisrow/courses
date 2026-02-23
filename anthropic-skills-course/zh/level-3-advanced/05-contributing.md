---
title: "向Anthropic贡献"
weight: 5
bookToc: true
---

# 向Anthropic贡献

## 简介

`anthropics/skills`仓库对贡献开放。

## 流程

### 步骤1：Fork

```bash
git clone https://github.com/YOUR-USERNAME/skills.git
```

### 步骤2：创建技能

遵循`template/SKILL.md`格式。添加`LICENSE.txt`（Apache 2.0）。

### 步骤3：Pull Request

```bash
git checkout -b add-my-skill
git add . && git commit -m "Add my-new-skill"
git push origin add-my-skill
```

PR中包含：技能功能说明、使用示例、测试结果。

## 改进现有技能

也可以修复指令、添加示例、改进描述或更新脚本。

## 总结

- Anthropic仓库对贡献开放
- 遵循标准Fork → Branch → PR流程
- 使用模板格式
- 也可以改进现有技能
