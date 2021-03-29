# Media Queries

## Hover

```css

.example {
	/* no hover styles */
}

@media (hover: hover) {
	.example:hover {
		/* can hover, so use hover styles */
	}
}
```

## Prefers-Reduced-Motion

- some users might have issues such as motion sickness and vertigo
- by reducing or removing motion of elements, authors can provide a more accessible experience
- this can be done via the `prefers-reduced-motion` media query

- `reduce` - allows authors to provide an alternative non-moving version of styles or no animations for elements

- Example: Using this query inside a `<picture>` element to provide a non-moving GIF for a11y

```html
<picture>
	<source srcset="no-motion.jpg" media="(prefers-reduced-motion: reduce)"></source>
	<img srcset="animated.gif" alt="brick wall animating">
</picture>
```

-----

## Sources

- [Reducing motion with the picture element](http://bradfrost.com/blog/post/reducing-motion-with-the-picture-element/)
- [Reducing Motion to Improve Accessibility - DEV Community 👩‍💻👨‍💻](https://dev.to/lkopacz/reducing-motion-to-improve-accessibility-1c0i)
