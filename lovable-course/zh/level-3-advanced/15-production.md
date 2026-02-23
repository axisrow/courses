---
title: "生产环境与扩展"
weight: 15
bookToc: true
---

# 生产环境与扩展

自信地将应用投入生产。

## 上线前检查清单

- [ ] 所有功能正常工作
- [ ] 认证安全
- [ ] 所有表设置了 RLS 策略
- [ ] 错误处理到位
- [ ] 移动端适配
- [ ] 自定义域名已配置
- [ ] SEO meta 标签已添加

## SEO

> 添加 meta 标签：title、description、Open Graph 标签用于社交分享。

## 环境变量

密钥不要写在代码中：
- Supabase 密钥 → Supabase 控制台
- API 密钥 → Edge Function secrets
- 永远不要提交 `.env` 文件

## 监控

| 工具 | 用途 |
|------|------|
| Supabase Dashboard | 数据库指标、认证日志 |
| Vercel Analytics | 页面浏览量、Web Vitals |
| Sentry | 错误追踪 |
| UptimeRobot | 可用性监控 |

## 扩展

- **数据库：** Supabase 在付费计划上自动扩展 PostgreSQL。
- **存储：** 随计划扩展。
- **Edge Functions：** 根据流量自动扩展。

## 备份

- Supabase Pro 计划每日自动备份。
- 定期导出 GitHub 仓库。
- 记录 Supabase 数据库架构。

## 成本规划

| 使用量级 | 估计费用 |
|---------|---------|
| 业余（< 1K 用户）| 免费 |
| 创业（< 10K 用户）| $25–50/月 |
| 增长（< 100K 用户）| $100–300/月 |

## 总结

做好安全、监控和扩展准备，让应用顺利上线。Lovable + Supabase 为你提供坚实的基础。

恭喜——你已完成全部课程！🎉
