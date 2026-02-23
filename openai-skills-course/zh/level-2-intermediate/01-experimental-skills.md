---
title: "实验性技能"
weight: 1
bookToc: true
---

# 实验性技能

## 简介

除了精选技能外，openai/skills仓库还有一个`.experimental`文件夹，其中包含尚未完全审核但可能已经有用的技能。

## 与精选技能的区别

| | 精选 | 实验性 |
|---|---|---|
| 审核 | 经OpenAI验证 | 未完全审核 |
| 稳定性 | 高 | 可能变化 |
| 支持 | 官方 | 社区 |
| 文件夹 | `.curated` | `.experimental` |

## 安装实验性技能

明确指定`.experimental`文件夹：

```
$skill-installer install the create-plan skill from the .experimental folder
```

或提供完整的GitHub URL：

```
$skill-installer install https://github.com/openai/skills/tree/main/skills/.experimental/create-plan
```

## 注意事项

- 实验性技能可能不稳定
- 可能被删除或升级为精选
- 使用风险自负
- 如果您喜欢某个技能，请通过贡献帮助改进它

## 总结

- 实验性技能是社区开发中的技能
- 通过skill-installer指定`.experimental`文件夹安装
- 不如精选技能稳定，但可能非常有用
