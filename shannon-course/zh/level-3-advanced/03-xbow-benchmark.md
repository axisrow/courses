---
title: "XBOW基准测试"
weight: 3
bookToc: true
---

# XBOW基准测试

## 简介

XBOW是一个包含104个易受攻击应用程序的开放基准测试，用于评估AI渗透测试智能体。Shannon Lite取得了**96.15%的成功率**（104个中成功100个）。

## 按漏洞类型的结果

| 类型 | 总数 | 成功 | 成功率 |
|------|------|------|--------|
| 授权缺陷 | 25 | 25 | 100% |
| SQL注入 | 7 | 7 | 100% |
| 盲SQL注入 | 3 | 3 | 100% |
| SSRF/配置错误 | 22 | 21 | 95.45% |
| XSS | 23 | 22 | 95.65% |
| SSTI | 13 | 12 | 92.31% |
| 命令注入 | 11 | 10 | 90.91% |

## 4个失败案例

- **XBEN-10（XSS）：** 错误判断JSFuck负载可行性
- **XBEN-22（SSTI）：** 将SSTI误分类为误报
- **XBEN-34（RFI）：** 将RFI与LFI混淆
- **XBEN-82（通过SSRF的命令注入）：** 误分类eval()风险

## 成本对比

| 指标 | 传统渗透测试 | Shannon |
|------|------------|---------|
| 成本 | $10,000+ | ~$16 |
| 时间 | 数周 | <1.5小时 |
| 频率 | 每年1-2次 | 每次部署 |

## 可重现性

- 清理后的基准测试：[KeygraphHQ/xbow-validation-benchmarks](https://github.com/KeygraphHQ/xbow-validation-benchmarks)
- 完整结果：[xben-benchmark-results](https://github.com/KeygraphHQ/shannon/tree/main/xben-benchmark-results)

## 总结

- 在严格、无提示的基准测试中取得96.15%的成功率
- 授权缺陷和SQL注入最佳（100%）
- 4个失败是分类问题，而非根本性限制
- 结果完全可重现
