# Dialog Element

> Also known as the "modal dialog"

## Syntax

```html
<dialog>
  I'm a hidden dialog, until opened!
</dialog>

<dialog open>
  Our cookie policy...nah just kidding!
</dialog>
```

## JavaScript Events

```js
const dialog = document.querySelector('dialog');
dialog.show();  // <= show it
dialog.close(); // <= hide it
dialog.showModal(); // <= show with a backdrop generated
```

## CSS

- The `::backdrop` pseudo-element can help style the backgroup when invoked using `.showModal()`

## Notes

- The <kbd>esc</kbd> key will close the dialog by default

-----

## Sources

- [Exploring HTML dialog element with examples](https://dev.to/atapas/exploring-html-dialog-element-with-examples-2c43)
