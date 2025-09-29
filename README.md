# Spreadsheet Catalog

Hosted catalog UI for Messari's Excel and Google Sheets plugins.

## Purpose

This repository hosts a static HTML page that displays the Messari data catalog. It's designed to be embedded as an iframe in both Excel and Google Sheets plugins, providing a single source of truth for the catalog interface.

## Setup

1. Enable GitHub Pages:
   - Go to Settings → Pages
   - Source: Deploy from `/docs` folder
   - Your site will be at: `https://ytoast.github.io/spreadsheet-catalog/`

2. The catalog will automatically fetch data from:
   ```
   https://api.messari.io/timeseries/v1/catalog?spreadsheet=true
   ```

## Integration

### Google Sheets
Update `code.gs`:
```javascript
function showSidebar() {
  const html = HtmlService.createHtmlOutput(
    '<iframe src="https://ytoast.github.io/spreadsheet-catalog/" style="width:100%;height:100%;border:none;"></iframe>'
  )
  .setTitle('Messari Data')
  .setWidth(300);
  SpreadsheetApp.getUi().showSidebar(html);
}
```

