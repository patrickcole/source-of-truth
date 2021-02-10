# Input

## Number

> &lt;input type="number"&gt; is only intended for amounts

> ...its value represents a quantity or amount (e.g., a price or a number of items).

> Use the regular &lt;input type=text&gt; element for codes, PINs, account numbers, identification numbers, and any other numeric value that doesn’t represent an amount.

The following snippet provides a pattern to match numeric values only using `type="text"`:

```html
<input type="text" pattern="[0-9]*" inputmode="numeric" />
```

Sources: [<sup>1</sup>](#source1)

-----

## Sources

<sup id="source1">1</sup> [Web Platform News - March 06, 2020](https://webplatform.news/issues/2020-03-06)
