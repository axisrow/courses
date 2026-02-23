---
title: "创建插件"
weight: 3
bookToc: true
---

# 创建插件

## 简介

Pi 支持通过扩展（Extensions）、技能（Skills）、提示模板（Prompt Templates）和主题（Themes）进行扩展。打包为 Pi Packages 通过 npm 分享。

## 扩展（Extensions）

扩展为代理添加新工具。在 `.pi/extensions/` 中创建文件：

```typescript
// .pi/extensions/time.ts
import { Type } from '@mariozechner/pi-ai';

export default {
  name: 'current_time',
  description: '返回当前时间',
  parameters: Type.Object({}),
  execute: async () => {
    return new Date().toISOString();
  },
};
```

## 技能（Skills）

技能是包含指令的文本文件：

```bash
mkdir -p .pi/skills
cat > .pi/skills/git.md << 'EOF'
使用 Git 时：
- 始终创建 feature 分支
- 编写有意义的提交消息
- 使用 conventional commits
EOF
```

## 提示模板

不同任务的自定义系统提示：

```bash
cat > .pi/prompts/reviewer.md << 'EOF'
你是代码审查员。分析代码的：
- 安全性
- 性能
- 可读性
EOF
```

## Pi Packages

将扩展打包为 npm 包：

```json
{
  "name": "my-pi-package",
  "pi": {
    "extensions": ["./extensions/"],
    "skills": ["./skills/"],
    "prompts": ["./prompts/"]
  }
}
```

## 总结

- 扩展添加工具
- 技能提供指令
- 提示模板定义行为
- Pi Packages 让你分享一切
