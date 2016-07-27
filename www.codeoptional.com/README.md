# Code Optional Site Archive

## URLs, generally

Appended `.html` to most names so they'll work with standard nginx `try_files`. Assuming this is "enough" for most things.

## URLs to map specially

- `www.codeoptional.com/episodes?format=RSS` (to `episodes.rss`)
- `www.codeoptional.com/?format=RSS` (to `index.rss`)

## URLs ignored

Remaining files in the archive with `?author=` appended are getting ignored, and returning normal `index.html`. This is fine for such a small site; at least nothing will 404.

## Notes for content adaptation

- Remove author links
- Most `index.html` references are wget artifacts
    - including `index.html?format=RSS`
