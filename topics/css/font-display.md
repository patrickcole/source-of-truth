# Font-Display

- determines how a font face is displayed on whether and when it is downloaded and ready to use
- font display timeline is based on a timer the browser tries to use a downloaded font face

- some terms to remember:

-- block period: if font face is not loaded, any element using the font will be *invisible* until custom font is loaded
-- swap period: if font face is not loaded, any element using the font will be *a fallback font* until custom font is loaded
-- failure period: font face is not loaded, fallback font is displayed

- the options are:

-- auto: display strategy is defined by the user agent
-- block: short block period (short invisible display) / infinite swap period (but can load custom font anytime)
-- swap: extremely small block period (very short invisible display) / infinite swap period (but can load custom font anytime)
-- fallback: extremely small block period (very short invisible display) / short swap period (small amount of time the custom font could be used, otherwise fallback will be used)
-- optional: extremely small block period (very short invisible display) / no swap period (never switches to custom font, if it doesn't load quick enough in block period)

-----

## Sources

- [font-display - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display)
