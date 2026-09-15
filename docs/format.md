# Snippet file format

Export and import use a small, flat YAML dialect. It is plain text, so you can
edit it in any editor and move it between iOS and Android.

```yaml
# snippet-keyboard-format: 2
## Greetings
- "👋 | filter:👋"
- "👋🤝 | Hi, thanks for your message. I'm Alex, what's your name?"
- "👋🙌 | Hi, thanks for your message. I'm Alex."

## Work
- "📅 | dynamic:https://example.com/today"
- "🔗 | https://example.com/book"
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

## Snippet kinds (iOS 1.3 / Android 1.2 and later)

The first line of the file is `# snippet-keyboard-format: 2`. The app writes
it for you; it tells the app to read the kinds below. A file without it is
treated as a 1.0 file (a bare `https://` text is dynamic) and converted the
next time it is saved.

| Text starts with | Kind | Tapping the bubble |
|---|---|---|
| `dynamic:https://…` | Dynamic | fetches the URL and inserts the response |
| `filter:👋` | Filter | shows only the snippets whose label contains `👋`; pick one and the list comes back |
| anything else | Text | inserts the text — a bare `https://…` link is inserted as a link |

`text:` in front of a text that itself starts with one of those words keeps
it literal. The app adds it when needed.

### Extracting one value from a dynamic snippet

A dynamic snippet may have a second line with a rule that picks one part of
the response. In the app, edit the snippet and use **Pick what to insert…**;
the rule is written for you. In YAML:

```yaml
- "💱 | dynamic:https://tygiausd.org\nafter \"USD chợ đen\" between \"<td class=\\\"text-right\\\">\" \" \" #2"
- "💲 | dynamic:https://api.example.com/rates\njson $.data.usd"
```

Rules: `json PATH`, `after TEXT between START END #N`, `regex PATTERN`. If
the rule finds nothing, the URL is inserted instead.

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

*Kinds, extraction and edge whitespace require iOS 1.3 / Android 1.2 or later.*
