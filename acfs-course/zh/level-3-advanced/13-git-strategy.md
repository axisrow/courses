---
title: "Git 策略和仓库管理"
weight: 13
bookToc: true
---

# Git 策略和仓库管理

## 为什么 Git 在代理编程中重要

多个 AI 代理同时写代码时，你需要可靠的版本控制。

### Git 基本模型

把 Git 想象成游戏的存档系统：
- **Commit** = 保存游戏
- **Branch** = 创建平行时间线
- **Merge** = 合并两条时间线
- **Push** = 上传存档到云端

### ACFS Git 工作流

```
main 分支（生产就绪代码）
    ├── feature/agent-claude-backend
    ├── feature/agent-codex-frontend
    └── feature/agent-gemini-tests
```

每个代理在自己的分支上工作。防止冲突。

### RU — 仓库工具

```bash
ru sync    # 同步所有仓库
ru commit  # AI 驱动的跨脏仓库提交
```

有 10+ 项目时，RU 通过自动化常规 git 操作节省大量时间。

### 最佳实践

1. **每个代理每个任务一个分支** — 防止冲突
2. **频繁提交** — 小而频繁的保存优于稀少而巨大的
3. **使用 Agent Mail 文件预留**
4. **合并前扫描** — 每个分支运行 UBS
5. **审查代理 PR** — 合并到 main 前始终审查

### CAAM — 云认证账户管理器

```bash
caam switch work      # 工作账号
caam switch personal  # 个人账号
```

### 关键要点

每个代理的工作用独立分支。RU 自动化管理多仓库。CAAM 处理身份切换。合并到 main 前始终审查代理代码。
