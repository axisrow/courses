---
title: "云端硬盘文件管理"
weight: 8
bookToc: true
---

# 云端硬盘文件管理

## 浏览文件

```bash
gog drive list
gog drive list --folder "项目文件"
gog drive list --type document
gog drive list --shared
```

## 上传和下载

```bash
gog drive upload report.pdf
gog drive upload report.pdf --folder "报告"
gog drive download FILE_ID -o ./local/
gog drive download FILE_ID --format pdf -o report.pdf
```

## 创建文件夹

```bash
gog drive mkdir "新项目"
gog drive mkdir "子文件夹" --parent "新项目"
```

## 分享文件

```bash
gog drive share FILE_ID --email colleague@company.com --role writer
gog drive share FILE_ID --email team@company.com --role reader
gog drive share FILE_ID --anyone --role reader   # 公开链接
```

## 搜索

```bash
gog drive search "年度报告"
gog drive search --type spreadsheet --modified-after 2025-01-01
```

## 移动和删除

```bash
gog drive move FILE_ID --to "归档"
gog drive delete FILE_ID
gog drive trash list
gog drive trash empty
```

## 练习

1. 上传一个文件到指定文件夹
2. 分享文件给同事（只读权限）
3. 搜索最近修改的电子表格
