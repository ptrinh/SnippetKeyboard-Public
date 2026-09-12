# Google Apps Script

A few lines of JavaScript running inside your Google account. Good when the
text lives in Sheets, Calendar or Gmail and you do not want to publish it.

## Steps

1. Go to [script.google.com](https://script.google.com), **New project**.
2. Replace the code with:

   ```js
   function doGet() {
     const sheet = SpreadsheetApp.openById("YOUR_SHEET_ID").getSheetByName("Sheet1");
     const text = sheet.getRange("A1").getDisplayValue();
     return ContentService.createTextOutput(text)
       .setMimeType(ContentService.MimeType.TEXT);
   }
   ```

3. **Deploy → New deployment → Web app**. Execute as **Me**, access
   **Anyone**. Authorize when asked.
4. Copy the web app URL (`https://script.google.com/macros/s/…/exec`) and
   paste into a Dynamic snippet.

## Notes

- "Anyone" means anyone with the URL. Treat it like a password.
- Google redirects the request once; the keyboard follows it.
- After editing the script, create a **new deployment** or the old code keeps
  running.
- Calendar example: `CalendarApp.getDefaultCalendar().getEventsForDay(new Date())`
  and join the titles with `\n`.
