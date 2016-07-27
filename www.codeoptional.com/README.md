# Code Optional Site Archive

## URLs, generally

Appended `.html` to most names so they'll work with standard nginx `try_files`.

## URLs to map specially

- `episodes?format=RSS`
- `?format=RSS`
- `index.html?format=RSS`

## URLs ignored

Remaining files in the archive with `?author=` appended are getting ignored, and returning normal `index.html`. This is fine for such a small site; at least nothing will 404.

## Notes for content adaptation

- Remove author links
