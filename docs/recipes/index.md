# Recipes for dynamic snippets

A dynamic snippet is a bubble whose text is an `https://` URL. Tapping it
fetches that URL and inserts whatever comes back as text. That is the whole
mechanism, so anything that can serve a line of text works.

Pick by how much you want to set up:

| Recipe | Setup | Good for |
|---|---|---|
| [Pipedream](pipedream.md) | 5 minutes, free tier | anything computed: dates, lookups, chaining other APIs |
| [GitHub Gist](gist.md) | 1 minute, no code | text you edit by hand from your phone |
| [Google Sheets](google-sheets.md) | 2 minutes, no code | a value from a spreadsheet |
| [Google Apps Script](apps-script.md) | 10 minutes, a few lines of JS | data from your own Google account (Sheets, Calendar) |
| [Val Town](val-town.md) | 2 minutes, one function | the same as Pipedream, in a code editor |

## What the app expects

- `https://` only.
- The response body is inserted as-is (first 100 characters on the free tier,
  uncapped on Pro). Return plain text, not HTML or JSON, unless you want that
  inserted literally.
- 4 second timeout. If the fetch fails, the URL itself is inserted instead.
- No headers or cookies are sent. Your endpoint must be reachable without
  login.

## Tips

- Set `Content-Type: text/plain; charset=utf-8`.
- Trim trailing newlines unless you want them inserted.
- Keep the URL secret if the content is: anyone with the URL can fetch it.
