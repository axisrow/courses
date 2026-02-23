---
title: "沙箱"
weight: 3
bookToc: true
---

# 沙箱

## 简介

**沙箱**是DeerFlow执行代码的隔离环境。就像计算机内部的一台单独的计算机，智能体可以在其中实验而不会损害您的文件或系统。

## 为什么需要沙箱？

- **安全**：代码在隔离环境中运行
- **干净**：每个会话都从头开始
- **可重现**：结果不依赖于您的系统状态
- **可审计**：所有智能体操作都被记录和可见

## 沙箱类型

### 本地沙箱

代码直接在您的机器上运行。

```yaml
sandbox:
  use: src.sandbox.local:LocalSandboxProvider
```

**优点**：快速，设置简单 | **缺点**：隔离性较低

### Docker沙箱

代码在Docker容器中运行——完全隔离。

```yaml
sandbox:
  use: src.community.aio_sandbox:AioSandboxProvider
```

**优点**：完全隔离，安全 | **缺点**：需要Docker，稍慢

### Kubernetes沙箱

用于生产环境——每个沙箱运行在单独的Kubernetes pod中。

## 虚拟路径

| 虚拟路径 | 说明 |
|----------|------|
| `/mnt/user-data/workspace/` | 工作目录 |
| `/mnt/user-data/uploads/` | 上传的文件 |
| `/mnt/user-data/outputs/` | 结果 |
| `/mnt/skills/` | 技能 |

## 沙箱生命周期

1. **获取**：会话开始时创建沙箱
2. **使用**：智能体在沙箱中工作
3. **释放**：会话结束时释放资源

通过**SandboxMiddleware**自动管理。

## 总结

- 沙箱确保安全的代码执行
- 三种类型：本地、Docker、Kubernetes
- 智能体使用虚拟路径工作
- 生命周期自动管理
- 生产环境推荐使用Docker沙箱
