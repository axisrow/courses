---
title: "使用 API"
weight: 6
bookToc: true
---

# 使用 API

## 什么是 API？

API（应用程序接口）是两个程序之间的通信方式。n8n 连接 Slack、Google Sheets 等服务时就是在使用它们的 API。

## HTTP Request 节点

### HTTP 方法

| 方法 | 用途 | 示例 |
|------|------|------|
| **GET** | 读取数据 | 获取用户列表 |
| **POST** | 创建数据 | 添加新记录 |
| **PUT** | 更新数据 | 修改用户名 |
| **DELETE** | 删除数据 | 删除记录 |

### GET 请求
1. 添加 **HTTP Request**
2. 方法：**GET**
3. URL：`https://jsonplaceholder.typicode.com/posts/1`
4. 点击 **Execute Step**

### POST 请求
1. 方法：**POST**
2. URL：`https://jsonplaceholder.typicode.com/posts`
3. Body 类型：**JSON**
4. Body：
```json
{
  "title": "我的文章",
  "body": "来自 n8n！",
  "userId": 1
}
```

## 认证

### API 密钥
添加请求头 `Authorization: Bearer YOUR_KEY`。

### OAuth2
用于 Google、Slack、GitHub：
1. **Settings → Credentials**
2. 添加凭据，选择服务
3. 完成授权流程

### n8n 凭据系统
- 创建一次，多个工作流复用
- 密钥加密存储

## JSON 数据

用表达式访问字段：
- `{{ $json.title }}` — 标题
- `{{ $json.data.items[0].name }}` — 嵌套数据
- `{{ $json.results.length }}` — 元素计数

## 分页

在 HTTP Request 设置中启用分页，自动获取所有页面。

## API 错误处理

- **401** — 认证失败
- **404** — 资源不存在
- **429** — 请求过多
- **500** — 服务器错误

启用 **Continue on Fail** 优雅处理错误。

## 练习

1. 从免费天气 API 获取数据
2. 提取温度和天气描述
3. 格式化为可读消息

## 小结

你已能使用任何 API。下一课学习数据转换。
