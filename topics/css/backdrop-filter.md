# Backdrop-Filter

- Provides the ability to add filter effects to the background or "backdrop" of an element
- Useful for the "frosted glass effect" that is used in desktop operating systems such as mac OS.
- Designs can utilize this to show depth or contrast with images, text and other content.
- Originally implemented in Safari and Edge browsers, the prefixed version was `-webkit-backdrop-filter`
- Chrome now supports (August 2019) via `background-filter`
- The foreground element must have some sort of transparency, otherwise the background filter will not be implemented
- The overlaying element will get a new stacking context (useful for z-index purposes)
- Consider the performance cost by implementing filters on the background, as they might not be necessary
- Can be combined with SVG filters as well
- Multiple filter effects can be applied in one declaration

## Feature Detection and Fallback

```css
@supports (backdrop-filter: none) {
	.background {
		backdrop-filter: blur(10px)
	}
}

@supports not (backdrop-filter: none) {
	.background {
		background-image: url('blurred-hero.jpg');
	}
}
```

### Traditional Technique using Filters (on foreground)
- - [How to create clipped, blurred background images in CSS | CodyHouse](https://codyhouse.co/blog/post/how-to-clipped-blurred-background-images-in-css)

## Examples

- [backdrop-filter demo](https://codepen.io/robinrendle/pen/LmzLEL)
- [ManipulateElement a javascript class for changing element position and size](https://codepen.io/netsi1964/pen/JqBLPK)

-----

## Sources

- [Create OS-style backgrounds with backdrop-filter  |  web.dev](https://web.dev/backdrop-filter/)
