# Input

## Attributes

Sources: [<sup>2</sup>](#source2)

### Autofocus

```html
<input type="text" name="username" autofocus>
```

### Required

```html
<input type="text" name="username" required>
```

### Readonly

```html
<input type="text" name="order_number" value="T938AD-343" readonly>
```

### Pattern

```html
<input type="text" name="username" pattern="[a-z]{1,10}" title="Username should only be lowercase letters">
```

### Placeholder

```html
<input type="email" name="email" placeholder="user@example.com">
```

### Maxlength

- Sets the maximum amount of allowable characters
- NOTE: Could use pattern as well with RegEx

```html
<input type="text" name="sku" maxlength="7" value="0123456">
```

### Min and Max

- Set minimum and maximum allowed values for input
- Can be used for numbers or date/times

```html
<input type="number" min="1" max="10">
<input type="date" min="2000-01-01" max="2021-12-31">
```

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
<sup id="source2">2</sup> [8 Useful HTML input Attributes, You must know.](https://dev.to/saifullah/8-useful-html-input-attributes-you-must-know-24k8)
