# DNS-Prefetch

> Establishing an IP address for a particular domain name can take a bit of time the first time around. Once the domain has completed DNS lookup, it will be cached; further increasing speed of loading

- Using `dns-prefetch`, developers can explicitly state which domains need to be prefetched

## Example

```html
<!-- Regular preconnection from a domain -->
<link rel="preconnect" href="https://cdn.example.com">
<!-- Doesn't hurt to also perform dns-prefetch -->
<link rel="dns-prefetch" href="https://cdn.example.com">
```

-----

## Sources

- [Establish network connections early to improve perceived page speed](https://web.dev/preconnect-and-dns-prefetch/)
