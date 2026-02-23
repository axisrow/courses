---
title: "你的第一个工作流"
weight: 3
bookToc: true
---

# 你的第一个工作流

## 目标

创建一个从网上获取随机笑话的工作流。

## 步骤一：新建工作流

1. 在浏览器中打开 n8n
2. 点击 **Add Workflow**
3. 命名为 "My First Workflow"

## 步骤二：添加触发器

1. 点击画布上的 `+`
2. 搜索 **Manual Trigger**
3. 添加到画布

## 步骤三：添加 HTTP 请求节点

1. 点击触发器右侧的 `+`
2. 搜索 **HTTP Request**
3. URL：`https://official-joke-api.appspot.com/random_joke`
4. 方法：**GET**
5. 点击 **Execute Step** 测试

你将看到包含 `setup` 和 `punchline` 字段的笑话。

## 步骤四：格式化输出

1. 在 HTTP Request 后添加 **Set** 节点
2. **Add Value** → **String**
3. 名称：`joke`
4. 值：`{{ $json.setup }} — {{ $json.punchline }}`

## 步骤五：运行

1. 点击 **Execute Workflow**
2. 所有节点应显示绿色对勾
3. 点击最后一个节点查看结果

## 数据流向

数据从左到右流动：

```
Manual Trigger → HTTP Request → Set
                 （获取数据）    （格式化）
```

## 保存

点击 **Save**（Ctrl+S）。

## 练习

- 更换 API 地址
- 在 Set 中添加更多字段
- 添加第三个节点

## 小结

你创建了第一个工作流！下一课将学习基本节点类型。
