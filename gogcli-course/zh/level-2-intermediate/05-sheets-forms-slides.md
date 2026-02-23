---
title: "表格、表单和幻灯片"
weight: 10
bookToc: true
---

# 表格、表单和幻灯片

## Google Sheets（表格）

### 读取数据

```bash
gog sheets get SPREADSHEET_ID
gog sheets get SPREADSHEET_ID --range "Sheet1!A1:D10"
gog sheets get SPREADSHEET_ID --range "Sheet1!A:A" --format csv
```

### 写入数据

```bash
gog sheets set SPREADSHEET_ID --range "A1" --values "你好,世界"
gog sheets append SPREADSHEET_ID --range "Sheet1" --values "新,一行,数据"
```

### 创建表格

```bash
gog sheets create "月度报告"
gog sheets create "预算" --sheet "一月" --sheet "二月"
```

## Google Forms（表单）

```bash
gog forms list
gog forms get FORM_ID
gog forms responses FORM_ID
gog forms responses FORM_ID --format csv > responses.csv
```

## Google Slides（幻灯片）

```bash
gog slides list
gog slides get PRESENTATION_ID
gog slides export PRESENTATION_ID --format pdf -o presentation.pdf
```

## 练习

1. 创建一个表格并添加几行数据
2. 读取表格数据并导出为 CSV
3. 将幻灯片导出为 PDF
