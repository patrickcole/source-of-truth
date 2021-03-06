# DOM

## Remove Child

`element.remove()`

A utility function can be created to remove all children of a parent element:

```js
function removeAllChildren(el) {
  while(el.firstElementChild) {
    el.firstElementChild.remove();
  }
}
```

## innerHTML

Using innerHTML to remove children or add children can have some performance issues.

## textContent

To remove inner children on an element, `textContent` tends to be much faster than `innerHTML`:

```js
el.innerHTML = "";    // tends to be slower
el.textContent = "";  // faster than above
```

## replaceChildren

```js
el.replaceChildren(); // replaces all children with nothing
```

## Element IDs Are Global Variables

When an element has a declared `id` attribute, the value given to that id is available as a global reference. For example:

```html
<main id="page"></main>
```

Using `console.log` and providing the `page` value, we can see that it returns the `DOMElement` of `<main>`:

```js
console.log(page);
// => <main id="page"></main>
```

This is true **as long as** no other variable or constant has been declared with the same value of `page`. Once `page` is declared somewhere in the JavaScript global scope, `page` is re-assigned.

```js
const page = `My Application Page`;
console.log(page);
// => `My Application Page`
// The reference to the DOMElement is no longer attached.
```

### Scope Review

As a reminder about scope, you can have a variable/const inside a function's scope and still use the global scope:

```js
console.log("Global Scope:", page);
// => "Global Scope:" <main id="page"></main>

function getPageReference() {
  const page = "My Application Page";
  console.log("From within function scope:", page);
  // => "From within function scope: My Application Page"
}

getPageReference();
```
