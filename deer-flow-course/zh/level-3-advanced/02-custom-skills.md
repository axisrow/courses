---
title: "创建自定义技能"
weight: 2
bookToc: true
---

# 创建自定义技能

## 简介

DeerFlow的内置技能可以覆盖很多任务，但真正的力量在于创建**您自己的技能**。在本课中，您将学习如何创建、测试和分享自定义技能。

## 技能结构

每个技能是一个包含`SKILL.md`文件的文件夹：

```
skills/custom/
└── my-skill/
    └── SKILL.md
```

### SKILL.md格式

```markdown
---
name: data-analysis
description: "带可视化的数据分析"
license: MIT
allowed-tools:
  - bash
  - read_file
  - write_file
  - present_files
---

# 数据分析

## 过程

1. 读取上传的数据文件
2. 确定数据类型和结构
3. 执行基本统计分析
4. 创建可视化（图表）
5. 撰写包含结论的报告
6. 将结果保存到/mnt/user-data/outputs/
```

## 逐步创建技能

### 步骤1：创建文件夹

```bash
mkdir -p skills/custom/email-writer
```

### 步骤2：创建SKILL.md

编写包含名称、描述、允许的工具和逐步指令的Markdown文件。

### 步骤3：启用技能

在`extensions_config.json`中：

```json
{
  "skills": {
    "email-writer": {
      "enabled": true
    }
  }
}
```

或通过API：

```bash
curl -X PUT http://localhost:2026/api/skills/email-writer \
  -H "Content-Type: application/json" \
  -d '{"enabled": true}'
```

### 步骤4：测试

重启DeerFlow并尝试使用您的新技能。

## 最佳实践

1. **具体明确** — 详细描述预期结果
2. **限制工具** — 仅列出真正需要的`allowed-tools`
3. **添加示例** — 在SKILL.md中包含预期输出样本
4. **使用编号步骤** — 帮助智能体遵循逻辑
5. **定义规则** — 明确说明格式、长度、语言、风格约束

## 分享技能

技能可以打包为`.skill`归档（ZIP）：

```bash
cd skills/custom/email-writer
zip -r email-writer.skill .
```

通过API安装：

```bash
curl -X POST http://localhost:2026/api/skills/install \
  -F "file=@email-writer.skill"
```

## 总结

- 自定义技能是`skills/custom/`中的Markdown文件
- 格式：YAML元数据 + 逐步指令
- 技能可通过配置或API启用/禁用
- 通过.skill归档分发
- 最佳实践：具体性、有限工具、示例
