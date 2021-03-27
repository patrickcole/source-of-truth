# Preload

- The idea of preloading assets, gives developer the flexibility to opt-in to preloading assets as soon as possible, therefore modifying the priority of resources being downloaded
- Preloading maintains resources in cache for future requests, therefore, reducing the number of re-requests of same resource
- By preloading, the browser applies the correct Content Security Policy to the resource, stating this resource can be used on the app or page
- Also sets the `Accept` request header, stating this resource is acceptable

## Syntax

- Using the `HTMLLinkElement` or `<link>` combined with both a `rel="preload"` and an `as` attribute
- Even though we are declaring a `<link>` element with `rel="preload"`, we still need to **use** the actual file being preloaded
- The actual usage is done as normal, in the case below, with a CSS stylesheet:

```html
<!-- Preload stylesheet -->
<link rel="preload" href="style.css" as="style">
<!-- Actually using the stylesheet -->
<link rel="stylesheet" href="style.css">
<!-- Without the line above, the stylesheet would not actually be applied, it would just be preloaded -->
```


- Resources that need to be preloaded are ideally those that are critical to the application or webpage, such as core styles
- Preloading will occur simultaneously as the DOM and CSSOM are being constructed. Since it's being simultaneously downloaded, it will be ready much faster when DOM/CSSOM is ready

## Types of Resources

The following list is resource types that can be preloaded:

- script
- style
- image
- font: _requires a `crossorigin` property_
- audio
- video
- document: _via `<frame>` or `<iframe>`_
- embed: _via `<embed>`_
- fetch
- object: _via `<object>`_
- track: _WebVTT files_
- worker: _Web or Shared Worker_

For some resources, a MIME-type might need to be added to distinguish the specific type of resource for the browser. For example:

```html
<link rel="preload" href="intro.mp4" as="video" type="video/mp4">
<link rel="preload" href="intro.webm" as="video" type="video/webm">
```

## Media Queries and Preloading

- Media query preloading will only decide if a resource should be preloaded or not based on query rule; it's up to JavaScript to apply actual resource from preloaded memory/cache
- [<sup>3</sup>](#source3) The use of a `<meta viewport>` tag must be applied **before** any preload `<link>` elements for media queries to be factored in
- Link elements can accept media query rules so resources will only be preloaded when acceptable query rule is in-place
- By utilizing media queries, higher-res preloading of resources can be skipped on lower size screens and save on downloading size

## Preloading Scripts

Sometimes you may want to preload a script that isn't being executed right away. This is important as you can speed up the time to DOMContentReady by reducing the amount of script to parse.

```js
let preloadLink = document.createElement('link');
preloadLink.href = "optional.js";
preloadLink.rel = "preload";
preloadLink.as = "script";
document.head.appendChild(preloadLink);
```

Once the `optional.js` is ready to be used or called, a much smaller script can be executed to dynamically build the `<script>` tag and bring in the preloaded data (via `.src`):

```js
function runOptional() {
  let preloadedScript = document.createElement('script');
  preloadedScript.src = "optional.js";
  document.body.appendChild(preloadedScript);

  // now any code inside optiona.js exists on your current page or app
}
```

-----

## Sources

- [Preloading content with rel="preload" - HTML: Hypertext Markup Language | MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content)
- [Building the DOM faster: speculative parsing, async, defer and preload - Mozilla Hacks - the Web developer blog](https://hacks.mozilla.org/2017/09/building-the-dom-faster-speculative-parsing-async-defer-and-preload/)
- <sup id="source3">3</sup>[Viewport and media query based preloading - Francis John - Medium](https://medium.com/@francis.john/viewport-and-media-query-based-preloading-87db30ff6d5f)
- [Preload: What Is It Good For? — Smashing Magazine](https://www.smashingmagazine.com/2016/02/preload-what-is-it-good-for/)
