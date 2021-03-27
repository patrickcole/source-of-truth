# Layout (DRAFT)

## Sub-Topics

- Parent/Child Relationship: `parent`, `child`
- Display: `block`, `inline`, `inline-block`, `flex`, `grid`
- Box-Model: `margin`, `padding`, `border`
- Position: `absolute`, `relative`, `fixed`
- Overflow
- Floats
- Flexbox
- Grid

### Parent/Child Relationship

CSS respects the DOM parent/child relationship between two elements when calculating styles. For example, a child block-level element will try to occupy all available space in the inline (or horizontal) direction. This is **by default** according to the rules of `display: block`.

As we go through more rules of CSS layout, keep in mind the relationship between elements in the DOM and how that affects their display with CSS.

Certain properties such as `color` will be handed down from a parent to its decedents, until any of those decedents change their `color` properties.

```html
<article>
  <h1>New Story!</h1>
  <p>This story is the <span>biggest</span> news to hit the market!</p>
</article>
```

```css
article {
  color: red;
}

span {
  color: rebeccapurple;
}
```

In the example above, the color of the header and most of the paragraph are `red`. However, since the span changed its color value to `rebeccapurple`, it will be purple.

> NOTE: Since we are using global `article` and `span` CSS selectors, every single `<article>` and its children would be red text and every `<span>` would be purple text.

Some properties that are inherited down from parent to children:

- `background-color`
- `color`
- `cursor`
- `font-family`
- `font-size`
- `letter-spacing`
- `text-transform`

#### Explicitly Inherit

Using `inherit` as a value on some properties, can grab the parent container's property and apply it to a child. **Be careful with this!** If an element changes its order in the DOM hierarchy, using `inherit` could yield unintended results.

For example, a parent is configured as `display: flex`. Each child element also wants to use flex for their display. One approach to this is to use `display: inherit` inside the child's CSS selector.

If the parent element changes to `display: block`, then the children would automatically change to `block` as well with no additional change required.

> ALERT: Be careful with inheriting size values such as `width` and `height`! CSS rules such as `display: block` will automatically try to fit the child element to the parent container's width.

Sources: [<sup>1</sup>](#source1)

### Display

Assuming a horizontal writing mode (left-to-right):

- `inline` renders elements horizontally (LR or RL)
- `block` renders elements vertically (TB or BT)

> Note: In vertical writing mode, `inline` and `block` switch their directions respectively.

Some examples of each display types:

- `block`: `<p>`, `<div>`, `<h1>`, `<article>`, `<main>`
- `inline`: `<span>`, `<a>`, `<img>`

Sources: [<sup>1</sup>](#source1)

### Box Model

#### Margin

##### Margin Collapse

Two elements that are block-level, share margins with their siblings. Between two elements, the larger margin value between the two will be the amount of space between the boxes.

> TODO: Add Example!
> TODO: show example of how borders render the boxes and no margin means that they line up next to each other with no spacing in-between.

#### Padding

#### Border

Sources: [<sup>1</sup>](#source1)

### Position

> Parent's position can affect how the children are displayed in the flow order of the page.

Sources: [<sup>3</sup>](#source3)

### Overflow

### Floats

Sources: [<sup>3</sup>](#source3)

### Flexbox

### Grid

-----

## Sources

<sup id="source1">1</sup> [MDN - Block and inline layout in normal flow](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flow_Layout/Block_and_Inline_Layout_in_Normal_Flow)
<sup id="source2">2</sup> [MDN - Flow Layout and Overflow](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flow_Layout/Flow_Layout_and_Overflow)
<sup id="source3">3</sup> [MDN - In Flow and Out of Flow](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flow_Layout/In_Flow_and_Out_of_Flow)
<sup id="source4">4</sup> [MDN - Introduction to the CSS basic box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)
