---
title: "第一次扫描"
weight: 4
bookToc: true
---

# 第一次扫描

## 简介

让我们对OWASP Juice Shop——一个故意存在漏洞的练习应用——进行完整的渗透测试。

## 第1步：启动Juice Shop

```bash
docker run -d -p 3000:3000 bkimminich/juice-shop
```

打开`http://localhost:3000`，您将看到一个在线果汁商店。

## 第2步：准备源代码

```bash
git clone https://github.com/juice-shop/juice-shop.git ./repos/juice-shop
```

## 第3步：运行Shannon

```bash
./shannon start URL=http://host.docker.internal:3000 REPO=juice-shop
```

## 第4步：观察过程

```bash
./shannon logs
```

过程大约需要1-1.5小时。Shannon经历4个阶段：
1. **侦察** — 映射应用程序，找到入口点
2. **漏洞分析** — 在代码中寻找潜在问题
3. **利用** — 尝试实际利用每个漏洞
4. **报告** — 将已证实的发现编入报告

## 第5步：获取结果

完成后，报告在：`audit-logs/{hostname}_{sessionId}/deliverables/`

## 使用工作区

测试中断后可以恢复：

```bash
./shannon start URL=http://host.docker.internal:3000 REPO=juice-shop WORKSPACE=my-test
```

## 总结

- 在练习应用上运行了完整的渗透测试
- 了解了Shannon的4个阶段
- 学会了使用工作区恢复测试
- 结果保存在`audit-logs/`目录
