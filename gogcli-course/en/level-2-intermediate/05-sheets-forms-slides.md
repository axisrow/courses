---
title: "Sheets, Forms & Slides"
weight: 10
bookToc: true
---

# Sheets, Forms & Slides

Work with spreadsheets, forms, and presentations from the terminal.

## Google Sheets

### Reading Data

```bash
# View spreadsheet metadata (sheet names, etc.)
gog sheets metadata SPREADSHEET_ID

# Read a cell range
gog sheets get SPREADSHEET_ID 'Sheet1!A1:D10'

# Read with JSON output for processing
gog sheets get SPREADSHEET_ID 'Sheet1!A1:D10' --json
```

### Writing Data

Use pipe `|` to separate columns and comma `,` to separate rows:

```bash
# Write to a specific cell
gog sheets update SPREADSHEET_ID 'A1' 'Hello'

# Write a row
gog sheets update SPREADSHEET_ID 'A1' 'Name|Age|City'

# Write multiple rows
gog sheets update SPREADSHEET_ID 'A1' 'Name|Age,Alice|30,Bob|25'

# Write from JSON
gog sheets update SPREADSHEET_ID 'A1' --values-json '[["Name","Age"],["Alice",30]]'

# Append a new row to the end
gog sheets append SPREADSHEET_ID 'Sheet1!A:C' 'Charlie|28|London'
```

### Formatting and Structure

```bash
# Bold a range
gog sheets format SPREADSHEET_ID 'Sheet1!A1:C1' \
  --format-json '{"textFormat":{"bold":true}}' \
  --format-fields 'userEnteredFormat.textFormat.bold'

# Insert 3 rows after row 2
gog sheets insert SPREADSHEET_ID "Sheet1" rows 2 --count 3

# Read cell notes
gog sheets notes SPREADSHEET_ID 'Sheet1!A1:B10'

# Clear a range
gog sheets clear SPREADSHEET_ID 'Sheet1!A1:B10'
```

### Creating and Exporting

```bash
# Create a new spreadsheet
gog sheets create "Budget 2025" --sheets "Income,Expenses"

# Copy a spreadsheet
gog sheets copy SPREADSHEET_ID "Budget Copy"

# Export as PDF
gog sheets export SPREADSHEET_ID --format pdf --out ./budget.pdf

# Export as Excel
gog sheets export SPREADSHEET_ID --format xlsx --out ./budget.xlsx
```

## Google Forms

### Creating a Form

```bash
gog forms create --title "Feedback Survey" --description "Please share your thoughts"
```

### Viewing Forms and Responses

```bash
# Get form details
gog forms get FORM_ID

# List responses
gog forms responses list FORM_ID --max 20

# Get a specific response
gog forms responses get FORM_ID RESPONSE_ID
```

## Google Slides

### Working with Presentations

```bash
# Get presentation info
gog slides info PRESENTATION_ID

# Create a new presentation
gog slides create "Q1 Review"

# Create from markdown
gog slides create-from-markdown "Quarterly Report" --content-file ./slides.md

# Copy a presentation
gog slides copy PRESENTATION_ID "Q1 Review Copy"

# List all slides
gog slides list-slides PRESENTATION_ID
```

### Adding and Editing Slides

```bash
# Add a slide from an image
gog slides add-slide PRESENTATION_ID ./chart.png --notes "Revenue chart"

# Update speaker notes
gog slides update-notes PRESENTATION_ID SLIDE_ID --notes "Talk about growth"

# Replace a slide's image
gog slides replace-slide PRESENTATION_ID SLIDE_ID ./updated-chart.png
```

### Exporting

```bash
# Export as PDF
gog slides export PRESENTATION_ID --format pdf --out ./deck.pdf

# Export as PowerPoint
gog slides export PRESENTATION_ID --format pptx --out ./deck.pptx
```

## Apps Script

For automation within Google Workspace:

```bash
# Create a project
gog appscript create --title "My Automation"

# View project content
gog appscript content SCRIPT_ID

# Run a function
gog appscript run SCRIPT_ID myFunction --params '["arg1", 123]'
```

## Next Steps

You've completed the Intermediate level! Move on to **Level 3: Advanced** to learn about scripting, multiple accounts, service accounts, and more.
