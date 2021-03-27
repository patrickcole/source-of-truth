# Prefetch

- Done via an `HTMLLinkElement` with a `rel` attribute of `prefetch`
- Purpose is to define resources that might be used/needed on the next page load
- A use-case might be a step-by-step wizard or configuration guide going one page to another

## Syntax

```html
<head>
  <link rel="prefetch" href="/images/step2-banner.jpg">
</head>
```

-----

## Sources

- [Preloading content with rel="preload" - HTML: Hypertext Markup Language | MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content)
