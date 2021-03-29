# HTTP Lifecycle

- Fetch document or resource
- Server responds with document in `binary stream format` containing response header(s)
- A HTML page would have `Content-Type: text/html; charset=UTF-8`
- `text/html` is the `MIME Type`
- `charset=UTF-8` is the character encoding
- these "clues" tell the browser how to render the page

So begins the Critical Rendering Path

- the data is fed to the parser to begin constructing the DOM
- any style-related nodes from the DOM begin the process of creating the CSSOM
- upon completion of the CSSOM, the RenderTree will be established
- the RenderTree begins the reflow state (and would repeat it upon scroll, resize, etc.)
- the Layer stage constructs the various levels along the z-axis, if they exist
- the paint stage begins building layers (in forms of tiles) so they can be added on-screen (this is repeated during what's called a reflow or repeat, usually on a scroll or update of the visual look of the page)
- the composition stage will assemble the layers so they match the proper location on-screen
- be aware of render-blocking resources such as CSS and JavaScript and how they can affect the CRP
- utilize `async` and `defer` for JS scripts
- use `preload` in `<head>` to prepare resources that will be used and referred to in CSS or JavaScript

## CSSOM (CSS Object Model)

- similar to the DOM, it creates a "tree-like" structure for all style declarations but for each DOM element that has a style attached to it
- will not contain elements that are not printed to screen, such as `<meta>`, `<script>`, `<title>`, etc.
- each browser supplies its own `user agent stylesheet` and then custom styles are applied on-top of the user agent declarations
- style rules cascade down from where they are declared
- child elements will inherit properties of their parents, if not declared explicitly on the child element
- rules are read from top-to-bottom and based on selector specificity, applied to elements
- specificity allows certain rules to override others based on how narrow the declaration should be

## DOM (Document Object Model)

- each tag in a HTML document is a node, essentially JavaScript objects
- each object has their own set of properties, methods and content embedded in them
- for example a `<div>` tag is an instance of the `HTMLDivElement` object, which is an instance of `Node` object
- each of these node objects are then constructed into a "tree-like" structure to show hierarchy of the nodes
- NOTE: Text inside nodes are treated as `TextNode`s, they are not Elements
- DOM is a high-level Web API provided by the browser, not part of JavaScript
- content bytes are loaded from top-to-bottom; any embedded CSS or JS will be parsed *synchronously*
- external stylesheets are requested via fetch *asynchronously* and the parser continues on
- external scripts pause parsing of the DOM until the full JavaScript file is *downloaded and parsed*
- `DOMContentLoaded` event is fired when the DOM has finished constructing
- `DOMContentLoaded` also fires when all external JS is parsed and DOM is fully ready
- `window.onLoad` fires when external stylesheets and files are downloaded and page is fully ready
- CSS is a render blocking resource, this means that rendering will pause while CSS is being loaded and parsed, therefore the `DomContentLoaded` event will not fire until rendering completes.

## Speculative Parsing

- the idea that some resources can be loaded even if the DOM will update or change
- this concept is very useful for items such as images that might take a while to load, but won't affect the DOM or CSSOM
- browsers utilize this along with `async/defer` and `preload` properties can speed up loading times for webpages

-----

## Sources

- [How the browser renders a web page? — DOM, CSSOM and Rendering](https://itnext.io/how-the-browser-renders-a-web-page-dom-cssom-and-rendering-df10531c9969)
- [Building the DOM faster: speculative parsing, async, defer and preload - Mozilla Hacks - the Web developer blog](https://hacks.mozilla.org/2017/09/building-the-dom-faster-speculative-parsing-async-defer-and-preload/)