# GitHub Gist

The simplest option when you just want text you can edit by hand, from your
phone, and have the snippet pick it up.

## Steps

1. Go to [gist.github.com](https://gist.github.com), create a gist with one
   file, e.g. `today.txt`. Public or secret both work; secret is not private,
   just unlisted.
2. Click **Raw**. The URL looks like
   `https://gist.githubusercontent.com/USER/ID/raw/COMMIT/today.txt`.
3. **Remove the commit hash** so the link always returns the latest version:
   `https://gist.githubusercontent.com/USER/ID/raw/today.txt`
4. Paste that into a Dynamic snippet.

Edit the gist in the GitHub app or web whenever the text changes. Updates can
take a minute or two to show up because of caching.
