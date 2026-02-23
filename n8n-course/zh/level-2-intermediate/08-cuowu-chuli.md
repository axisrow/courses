---
title: "错误处理"
weight: 8
bookToc: true
---

# 错误处理

## 为什么要处理错误？

外部服务随时可能出错。没有错误处理，一个故障就会停止整个工作流。

## 错误类型

- **连接错误** — 无法访问服务
- **认证错误** — 凭据无效
- **数据错误** — 格式不符预期
- **限流** — 请求过多
- **超时** — 服务响应太慢

## 内置机制

### Continue on Fail
在节点 **Settings** 中启用：
- 节点捕获错误而不停止
- 下一个节点收到错误信息
- 工作流继续运行

### Retry on Fail
- 设置重试次数（如 3 次）
- 设置重试间隔
- 适用于临时故障

## Error Workflow

全局错误处理器：

1. 创建单独的工作流
2. 以 **Error Trigger** 节点开始
3. 添加操作：Slack 提醒、邮件通知、写入数据库
4. 在主工作流 **Settings → Error Workflow** 中选择

## IF 节点验证

```
IF → $json.email 包含 "@"
   True → 继续处理
   False → 错误通知
```

## 错误处理模式

### 失败通知
```
主工作流 → Error Workflow → Slack / Email
```

### 默认值回退
```
HTTP Request（可能失败）→ IF（有错误？）→ 是：设默认值
                                         → 否：正常继续
```

### 死信队列
```
失败项 → 保存到 Google Sheet 待人工审查
```

## 监控执行

1. 左侧菜单 **Executions**
2. 筛选 **Failed**
3. 点击查看哪个节点出错及原因
4. 修复后重新运行

## 练习

1. 调用错误 URL：`https://httpstat.us/500`
2. 启用 **Continue on Fail**
3. 添加 **IF** 检查错误
4. 出错时用 Set 记录错误信息
5. 创建 Error Workflow 发送通知

## 小结

工作流现在能抵御错误了。下一课学习条件逻辑。
