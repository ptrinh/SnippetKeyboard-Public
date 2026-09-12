# Snippet file format

Export and import use a small, flat YAML dialect. It is plain text, so you can
edit it in any editor and move it between iOS and Android.

```yaml
## Greetings
- "👋 | Hi, thanks for your message."
- "🙏 | Thanks, speak soon."

## Work
- "📅 | https://example.com/today"
- "plain text with no label"
```

## Rules

| Line | Meaning |
|---|---|
| `## Name` | starts a category |
| `- "label | text"` | a snippet; the label is what the bubble shows |
| `- "text"` | a snippet with no label; the bubble shows the text |
| `# comment`, blank line | ignored |

- `\n` inside the text is a line break.
- A `|` inside your text is written as `\|`. The app does this for you on export.
- Text starting with `https://` is a dynamic snippet: tapping it fetches the
  URL and inserts the response.

## Spaces and blank lines

Quotes are what preserve spaces at the start or end of the text. Inside
quotes, the text is taken exactly as written:

```yaml
- "Sign-off | Thanks   "        # keeps three trailing spaces
- "Gap | \n\n"                  # inserts two blank lines
- "Both |   Hello\n\nThanks\n\n"
```

Without quotes, leading and trailing spaces are trimmed.

This is useful when you build a reply from several snippets in a row: end
each piece with the spacing the next one needs.

*Requires version 1.0.1 or later. Earlier versions trimmed these.*
