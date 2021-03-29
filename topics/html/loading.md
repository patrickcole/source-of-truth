# Loading

## Loading Stylesheets Based on Media Queries

- the `media` attribute only decides when the resource is being applied, the resource will always load if it is declared
- https://stackoverflow.com/a/47704047/6632985

## Lazy Loading

<a href="#source1"><sup>1</sup></a>

## Async Loading of Styles

- <a href="#source2"><sup>2</sup></a>prevents the styles from blocking the DOM (which is the default behavior of a stylesheet loading)
- this effectively loads the styles when the document's `onload` event occurs
- the file is still downloaded in the background, but not applied until the `onload`

`<link rel="stylesheet" href="secondary.css" media="none" onload="if(media !== 'all') media='all'">`

- as this is using JavaScript, a `<noscript>` declaration can be added underneath, if JS is not available
- the page will be repainted upon load of the async loaded stylesheet, but this should only happen the first time the cache is created
- each subsequent load will be from the cache and take less time/painting
- one use case for this technique is to load fonts asynchronously and still showing a fallback font while loading the font

```html
<link rel="stylesheet" href="main.css">
<link rel="stylesheet" href="font.css" media="none" onload="if(media!='all')media='all'">
```

- The `font.css` contains the `@font-face` declaration that updates the text to the new font
- Note: this technique might be deprecated in favor of new ways to load fonts


-----

## Sources

- <sup id="source1">1</sup>[AddyOsmani.com - Native image lazy-loading for the web!](https://addyosmani.com/blog/lazy-loading/)
- <sup id="source2">2</sup>[Loading CSS without blocking render](https://keithclark.co.uk/articles/loading-css-without-blocking-render/)
