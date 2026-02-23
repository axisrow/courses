---
title: "基本节点"
weight: 4
bookToc: true
---

# 基本节点

## 什么是节点？

节点是工作流的构建模块。每个节点执行一个任务。将节点连接起来就能创建强大的自动化。

## 节点分类

### 触发节点
启动工作流：
- **Manual Trigger** — 手动点击按钮
- **Schedule Trigger** — 定时运行
- **Webhook** — 接收外部 HTTP 请求

### 操作节点
执行具体工作：
- **HTTP Request** — 调用任意 API
- **Set** — 创建和修改字段
- **IF** — 条件判断
- **Code** — 自定义 JavaScript 或 Python
- **Merge** — 合并数据

### 应用节点
连接特定服务：
- **Gmail** — 收发邮件
- **Slack** — 发送频道消息
- **Google Sheets** — 读写表格
- **Notion** — 管理页面和数据库
- **GitHub** — 操作仓库和 Issue

## 最重要的节点

### HTTP Request
最通用的节点，可连接任何 API。

### Set
重塑数据：重命名字段、添加新字段、删除多余字段。

### IF
根据条件分两条路径：
- **True** — 条件成立
- **False** — 条件不成立

示例：如果 `status` = "紧急" → Slack 提醒，否则 → 记录到表格。

## 如何添加节点

1. 点击 `+`
2. 搜索或浏览
3. 配置参数
4. 点击 **Execute Step** 测试

## 练习

构建：**Manual Trigger** → **Set**（姓名和年龄）→ **IF**（年龄 > 18）→ 两个 **Set**（"成人" 和 "未成年"）。

## 小结

你已了解主要节点类型。下一课学习触发器和定时调度。
