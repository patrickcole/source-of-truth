# Preconnect

- Inform the browser that the page will make connections to a specific domain address
- Can speed up creating connections to additional host machines and therefore increasing performance
- Multiple connections to the same preconnected domain will load faster as the connection has already been established

## When To Use

- Developers know where resources are coming from, for example: a CDN that might respond back with useful resources for app/page
- Streaming media domains
- Fonts will need to be preconnected with `crossorigin` attribute

## Additional Notes

- Do not preconnect to your own domain, this is trivial
- Any connections left open, are only open for ~ 10 seconds; use of a connection will need to occur during that lifespan

## Syntax

```html
<head>
  <link rel="preconnect" href="https://cdn.example.com">
</head>
```

-----

## Sources

- [Establish network connections early to improve perceived page speed](https://web.dev/preconnect-and-dns-prefetch/)
