---
title: "测试技能"
weight: 3
bookToc: true
---

# 测试技能

## 简介

测试是技能创建的关键步骤。经过良好测试的技能工作可靠且可预测。

## 第1步：验证结构

运行`quick_validate.py`：

```bash
python scripts/quick_validate.py ./my-skill
```

检查内容：SKILL.md存在、YAML frontmatter正确、必填字段、命名规则。

## 第2步：测试脚本

运行`scripts/`中的每个脚本并验证：

```bash
python scripts/my_script.py --help
python scripts/my_script.py test_data.csv
python scripts/my_script.py empty.csv
```

## 第3步：在Codex中测试

在本地安装技能并在实际条件下验证：

```bash
cp -r ./my-skill ~/.codex/skills/
```

检查：是否在正确的请求上触发？是否正确执行？是否有误触发？

## 第4步：评估

一些精选技能包含`evaluations/`文件夹，其中有用于自动测试的JSON文件。

## 第5步：迭代

1. 在实际任务中使用技能
2. 注意问题
3. 更新SKILL.md和脚本
4. 再次测试

## 测试清单

- [ ] `quick_validate.py`通过
- [ ] 所有脚本正确运行
- [ ] 技能在正确的请求上触发
- [ ] 没有误触发
- [ ] 处理了边界情况
- [ ] 在实际任务中测试过

## 总结

- 从`quick_validate.py`结构验证开始
- 手动测试每个脚本
- 在真实Codex使用中验证技能
- 基于经验迭代改进
