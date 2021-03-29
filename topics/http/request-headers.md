# HTTP Request Headers

## Link

- Provides the ability to send `<link>` elements through HTTP headers
- Examples:

```
Link: <some-document.html>;rel=prefetch
Link: <magic.css>;rel=stylesheet
```

## Range

Allows to request a range of bytes for a specified resource. For example `bytes=0-200` will request the first 200 bytes of a resource.

`curl www.google.com/robots.txt -H "Range: bytes=0-200"`

Useful for resuming downloads that were interrupted as new request doesn't have to start at beginning, could resume at where it left of using range header. The `wget` module utilizes this with the `--continue` call.

## Sources

- Julia Evans @b0rk on Twitter
- [Using CSS without HTML · Mathias Bynens](https://mathiasbynens.be/notes/css-without-html)
