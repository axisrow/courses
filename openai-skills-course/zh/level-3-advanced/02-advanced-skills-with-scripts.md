---
title: "带脚本的高级技能"
weight: 2
bookToc: true
---

# 带脚本的高级技能

## 简介

简单技能只包含文本指令。对于需要精确性和可重复性的任务，技能可以包含脚本——Python、Bash或其他语言的可执行代码。

## 何时添加脚本

- 相同的代码每次都需要重新编写
- 任务需要确定性结果
- 复杂逻辑无法仅用文本描述

## 带脚本的技能结构

```
my-advanced-skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── scripts/
│   ├── process_data.py
│   └── generate_report.py
├── references/
│   └── api_docs.md
└── assets/
    └── template.html
```

## 示例：CSV分析器技能

### SKILL.md

```markdown
---
name: csv-analyzer
description: 分析CSV文件——统计、过滤、可视化。当用户要求分析、汇总或可视化CSV数据时使用。
---

# CSV Analyzer

分析和可视化CSV文件中的数据。

## 使用方法

基本统计：
\`\`\`bash
python scripts/analyze.py data.csv
\`\`\`

可视化：
\`\`\`bash
python scripts/analyze.py data.csv --chart bar --column revenue
\`\`\`
```

### scripts/analyze.py

```python
#!/usr/bin/env python3
import csv, argparse

def analyze(filepath, column=None):
    with open(filepath) as f:
        rows = list(csv.DictReader(f))
    print(f"行数: {len(rows)}")
    print(f"列数: {len(rows[0]) if rows else 0}")
    if column and rows:
        values = [r[column] for r in rows if column in r]
        print(f"'{column}'中的唯一值: {len(set(values))}")

if __name__ == "__main__":
    parser = argparse.ArgumentParser()
    parser.add_argument("file")
    parser.add_argument("--column")
    args = parser.parse_args()
    analyze(args.file, args.column)
```

## 总结

- 脚本为技能提供精确性和可重复性
- 将脚本放在`scripts/`文件夹中
- 在SKILL.md中描述脚本及其参数
- 使用`references/`存放大型参考材料
- 发布前测试每个脚本
