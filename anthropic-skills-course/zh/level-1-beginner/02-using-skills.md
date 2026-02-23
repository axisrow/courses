---
title: "在Claude Code、Claude.ai和API中使用"
weight: 2
bookToc: true
---

# 使用Skills

## 简介

Skills可以通过三种方式使用：Claude Code（CLI）、Claude.ai网页界面和API。

## Claude Code

```bash
# 添加市场
/plugin marketplace add anthropics/skills

# 安装技能
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

安装后，只需在请求中提到相关任务即可。

## Claude.ai

付费用户可直接使用内置技能。自定义技能通过项目设置上传。

## Claude API

通过API参数连接技能。详见[Skills API快速入门](https://docs.claude.com/en/api/skills-guide)。

## 总结

- Claude Code：通过`/plugin`命令安装
- Claude.ai：付费计划内置
- API：通过请求参数连接
- 技能在提到相关任务时自动激活
