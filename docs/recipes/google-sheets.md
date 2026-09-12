# Google Sheets

Publish one cell or range and read it as text. No code.

## Steps

1. In your sheet, put the text you want in a single cell, e.g. `Sheet1!A1`.
2. **File → Share → Publish to web**. Choose the sheet, format **Comma-separated
   values (.csv)**, and publish.
3. Copy the URL. Add `&range=A1` at the end so only that cell is returned:
   `https://docs.google.com/spreadsheets/d/e/…/pub?gid=0&single=true&output=csv&range=A1`
4. Paste into a Dynamic snippet.

## Notes

- Published sheets are public to anyone with the link.
- Text containing commas or quotes comes back CSV-quoted. If that bothers
   you, use [Apps Script](apps-script.md) instead and return plain text.
- Google caches published data for a few minutes.
