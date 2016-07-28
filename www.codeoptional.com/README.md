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
    - search for `class="author"`
- Most `index.html` references are wget artifacts
    - including `index.html?format=RSS`
    - search for `index.html`
- CSS
- Search for any `static` URLs

## Adaptation

### index.html todo

- CSS
- search for `static` URLs
- mirror to `episodes/index.html`, replacing

## nginx

I've been working with this config to try and maintain URLs and content-types:

```
server {
    listen 80;
    server_name codeoptional.com;

    return 301 http://www.codeoptional.com$request_uri;
}

server {
    listen       80;
    server_name  www.codeoptional.com;

    root   /home/cdzombak/www/codeoptional.com/public;

    location / {
        try_files "${uri}_${args}.rss" "${uri}index.html_${args}.rss" $uri $uri/ $uri/index.html $uri.html;
    }

    include drop.conf;
    include caching.conf;
}
```
