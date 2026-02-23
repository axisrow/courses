---
title: "Google Drive & Files"
weight: 8
bookToc: true
---

# Google Drive & Files

Upload, download, organize, and share files — all from the terminal.

## Browsing Files

```bash
# List recent files
gog drive ls --max 20

# List files in a specific folder
gog drive ls --parent FOLDER_ID --max 20

# Only your personal Drive (skip shared drives)
gog drive ls --no-all-drives

# Search for files
gog drive search "quarterly report" --max 10

# Search with raw query (advanced)
gog drive search "mimeType = 'application/pdf'" --raw-query
```

## Getting File Info

```bash
# File metadata
gog drive get FILE_ID

# Get the web URL
gog drive url FILE_ID
```

## Downloading Files

```bash
# Download a file
gog drive download FILE_ID --out ./myfile.pdf

# Export Google Docs as PDF
gog drive download DOC_ID --format pdf --out ./document.pdf

# Export as Word document
gog drive download DOC_ID --format docx --out ./document.docx

# Export Google Slides as PowerPoint
gog drive download SLIDES_ID --format pptx --out ./presentation.pptx
```

## Uploading Files

```bash
# Upload to a folder
gog drive upload ./report.pdf --parent FOLDER_ID

# Upload and convert to Google format
gog drive upload ./report.docx --convert

# Replace an existing file (keeps the same link)
gog drive upload ./report-v2.pdf --replace FILE_ID
```

## Organizing Files

```bash
# Create a folder
gog drive mkdir "Q1 Reports"

# Create a subfolder
gog drive mkdir "January" --parent FOLDER_ID

# Rename a file
gog drive rename FILE_ID "Better Name"

# Move a file to a different folder
gog drive move FILE_ID --parent DESTINATION_FOLDER_ID

# Delete (move to trash)
gog drive delete FILE_ID

# Permanently delete
gog drive delete FILE_ID --permanent
```

## Sharing and Permissions

```bash
# View current permissions
gog drive permissions FILE_ID

# Share with a specific person (read only)
gog drive share FILE_ID --to user --email colleague@example.com --role reader

# Share with edit access
gog drive share FILE_ID --to user --email colleague@example.com --role writer

# Share with entire domain
gog drive share FILE_ID --to domain --domain example.com --role reader

# Remove sharing
gog drive unshare FILE_ID --permission-id PERMISSION_ID
```

## Working with Google Docs

```bash
# Get document info
gog docs info DOC_ID

# Read document text
gog docs cat DOC_ID

# Create a new document
gog docs create "Meeting Notes"

# Create from markdown file
gog docs create "Report" --file ./report.md

# Copy a document
gog docs copy DOC_ID "Report Copy"

# Export as PDF
gog docs export DOC_ID --format pdf --out ./doc.pdf
```

## Working with Sheets

```bash
# View sheet metadata
gog sheets metadata SPREADSHEET_ID

# Read a range
gog sheets get SPREADSHEET_ID 'Sheet1!A1:D10'

# Write data (pipe-delimited: | separates columns, comma separates rows)
gog sheets update SPREADSHEET_ID 'A1' 'Name|Age,Alice|30,Bob|25'

# Append a row
gog sheets append SPREADSHEET_ID 'Sheet1!A:C' 'Charlie|28|Engineer'

# Create a new spreadsheet
gog sheets create "Budget 2025" --sheets "Income,Expenses,Summary"
```

## Shared Drives

```bash
# List shared drives (Team Drives)
gog drive drives --max 100
```

## Next Steps

In the next lesson, you'll learn to manage Contacts and Tasks.
