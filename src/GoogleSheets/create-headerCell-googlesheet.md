Here's the updated `batchUpdate` JSON to make headers **bold and centered** in one step:

## Complete Solution - Bold + Centered Headers

**HTTP Request Node:**
- Method: `POST`
- URL: `https://sheets.googleapis.com/v4/spreadsheets/{spreadsheetId}:batchUpdate`
- Content-Type: `application/json`

**JSON Body:**
```json
{
  "requests": [
    {
      "updateCells": {
        "range": {
          "sheetId": 0,
          "startRowIndex": 0,
          "endRowIndex": 1,
          "startColumnIndex": 0,
          "endColumnIndex": 3
        },
        "rows": [
          {
            "values": [
              {
                "userEnteredValue": {"stringValue": "Header1"},
                "userEnteredFormat": {
                  "textFormat": {"bold": true},
                  "horizontalAlignment": "CENTER"
                }
              },
              {
                "userEnteredValue": {"stringValue": "Header2"},
                "userEnteredFormat": {
                  "textFormat": {"bold": true},
                  "horizontalAlignment": "CENTER"
                }
              },
              {
                "userEnteredValue": {"stringValue": "Header3"},
                "userEnteredFormat": {
                  "textFormat": {"bold": true},
                  "horizontalAlignment": "CENTER"
                }
              }
            ]
          }
        ],
        "fields": "userEnteredValue,userEnteredFormat.textFormat.bold,userEnteredFormat.horizontalAlignment"
      }
    }
  ]
}
```

## Other Alignment Options:

If you want different alignment, replace `"CENTER"` with:
- `"LEFT"` - Left aligned
- `"RIGHT"` - Right aligned
- `"CENTER"` - Center aligned

## Bonus: Complete Header Styling

If you want even more professional headers (bold, centered, background color):

```json
{
  "requests": [
    {
      "updateCells": {
        "range": {
          "sheetId": 0,
          "startRowIndex": 0,
          "endRowIndex": 1,
          "startColumnIndex": 0,
          "endColumnIndex": 3
        },
        "rows": [
          {
            "values": [
              {
                "userEnteredValue": {"stringValue": "Header1"},
                "userEnteredFormat": {
                  "textFormat": {"bold": true},
                  "horizontalAlignment": "CENTER",
                  "backgroundColor": {
                    "red": 0.9,
                    "green": 0.9,
                    "blue": 0.9
                  }
                }
              },
              {
                "userEnteredValue": {"stringValue": "Header2"},
                "userEnteredFormat": {
                  "textFormat": {"bold": true},
                  "horizontalAlignment": "CENTER",
                  "backgroundColor": {
                    "red": 0.9,
                    "green": 0.9,
                    "blue": 0.9
                  }
                }
              },
              {
                "userEnteredValue": {"stringValue": "Header3"},
                "userEnteredFormat": {
                  "textFormat": {"bold": true},
                  "horizontalAlignment": "CENTER",
                  "backgroundColor": {
                    "red": 0.9,
                    "green": 0.9,
                    "blue": 0.9
                  }
                }
              }
            ]
          }
        ],
        "fields": "userEnteredValue,userEnteredFormat"
      }
    }
  ]
}
```

This gives you **bold, centered headers with a light gray background** - all in one API call!