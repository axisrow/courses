---
title: "为openai/skills做贡献"
weight: 5
bookToc: true
---

# 为openai/skills做贡献

## 简介

如果您创建了有用的技能，可以将其提交到官方[openai/skills](https://github.com/openai/skills)仓库。

## 社区价值观

- **友善和包容** — 尊重其他贡献者
- **假设善意** — 书面沟通很难
- **教与学** — 如果有困惑，开issue或PR

## 贡献流程

### 第1步：Fork仓库

访问[github.com/openai/skills](https://github.com/openai/skills)并点击"Fork"。

### 第2步：克隆Fork

```bash
git clone https://github.com/your-username/skills.git
cd skills
```

### 第3步：创建分支

```bash
git checkout -b add-my-skill
```

### 第4步：添加技能

将技能放入相应文件夹：

- `skills/.experimental/` — 新的实验性技能
- `skills/.curated/` — 仅通过邀请或审核后

```bash
cp -r ~/my-skill skills/.experimental/my-skill
```

### 第5步：验证

```bash
python skills/.system/skill-creator/scripts/quick_validate.py skills/.experimental/my-skill
```

### 第6步：创建Pull Request

```bash
git add .
git commit -m "Add my-skill to experimental"
git push origin add-my-skill
```

在GitHub上创建Pull Request。

## 安全

发现漏洞请发邮件至**security@openai.com**。不要在公开issue中发布漏洞。

## 技能之路

```
您的创意 → experimental → (审核) → curated → (可能) system
```

## 总结

- 贡献从fork和Pull Request开始
- 新技能添加到`.experimental`
- 遵循社区价值观
- 优秀的实验性技能可能升级为精选
- 安全问题发送至security@openai.com
