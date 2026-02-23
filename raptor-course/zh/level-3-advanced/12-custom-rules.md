---
title: "编写自定义 Semgrep 和 CodeQL 规则"
weight: 2
bookToc: true
---

## 编写自定义 Semgrep 和 CodeQL 规则

### 为什么需要自定义规则？

RAPTOR 的内置规则覆盖常见漏洞，但你的应用可能有需要自定义检测的独特模式。

### 自定义 Semgrep 规则

Semgrep 规则用 YAML 编写:

```yaml
rules:
  - id: my-custom-rule
    pattern: |
      dangerous_function($INPUT)
    message: "不可信输入传递给 dangerous_function"
    severity: ERROR
    languages: [python]
    metadata:
      category: security
      cwe: CWE-78
```

#### 将规则添加到 RAPTOR

将自定义规则放在:
```
engine/semgrep/rules/your-category/your-rule.yaml
```

### 自定义 CodeQL 查询

CodeQL 查询使用类 SQL 语言 QL:

```ql
import python
import semmle.python.dataflow.new.DataFlow

from DataFlow::Node source, DataFlow::Node sink
where
  source.asExpr() instanceof UserInput and
  sink.asExpr() = dangerousCall.getAnArgument()
select sink, "不可信数据流向危险函数"
```

### SARIF 合并工具

RAPTOR 包含 SARIF 合并工具（`engine/semgrep/tools/sarif_merge.py`），将多个扫描器的结果合并为单一报告。

### 测试自定义规则

1. 编写包含漏洞模式的测试文件
2. 放入 `test/data/`
3. 对其运行规则
4. 验证能检测到问题且无误报

### 核心要点

自定义规则让你可以针对特定代码库调整 RAPTOR。从 Semgrep 规则开始（更容易编写），然后进阶到 CodeQL 进行数据流分析。
