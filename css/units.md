### Absolute units

Absolute units always the same in any context. `px` is an absolute unit because the size of a pixel doesn’t change relative to anything else on the page. In fact, `px` is the only absolute unit you should be using for web projects. The rest of them make more sense in a print setting because they are related to physical units such as `in` (inch) and `cm` (centimeter).

### Relative units

Relative units are units that can change based on their context. There are several of them that you are likely to encounter and want to use.
#### em and rem

`em` and `rem` both refer to a font size, though they are often used to define other sizes in CSS. You’ll see both of them often so we’re going to explain both, but as a rule-of-thumb, prefer `rem`.

`1em` is the `font-size` of an element (or the element’s parent if you’re using it to set `font-size`). So, for example, if an element’s `font-size` is `16px`, then setting its width to `4em` would make its width `64px` (`16 * 4 == 64`).

`1rem` is the `font-size` of the root element (either `:root` or `html`). The math works the same with `rem` as it did with `em`, but without the added complexity of keeping track of the parent’s font size.

**useful shorthand**
- **em**: "my parent element's font-size" in the case of typography
- **rem**: "**The root element's font-size**" in the case of typography
#### Viewport units

The units `vh` and `vw` relate to the size of the viewport. Specifically, `1vh` is equal to `1%` of the viewport height and `1vw` is equal to `1%` of the viewport width. These can be useful any time you want something to be sized relative to the viewport, examples including full-height heroes, full-screen app-like interfaces.

#### Line height units
`lh` and `rlh` are relative lengths units similar to `em` and `rem`. The difference between `lh` and `rlh` is that the first one is relative to the line height of the element itself, while the second one is relative to the line height of the root element, usually `<html>`.

```css
p {
  margin: 0;
  background-image: repeating-linear-gradient(
    to top,
    lightskyblue 0 2px,
    transparent 2px 1lh
  );
}

```

#### Percentages
if you set an element's `font-size` as a percentage, it will be a percentage of the `font-size` of the element's parent. If you use a percentage for a `width` value, it will be a percentage of the `width` of the parent.

### Which units should you use?

Depends on the situation/property...

* **Font-size**: It's best to use rems - rem adapts to the user's preferences
	* If you don't want to perform calculations based on the 16px base html element, you can set the root html font size to 62.5% which sets the base font size to 10px.
		* 2.1rem = 21 pixels, makes the math easier.
* **Width**: most of the time a percentage and `max-width` are a good choice.
	* The `ch` unit could also be used, which is roughly equal to the width of a character of a font. This is useful for setting the number of characters per line to maximize readability -- `max-width: 45ch`
* **Height**: may not need to set height, use `min-height` if possible. Percentages, `rem`, or `vh` can work.
* **Padding or Margin**: use `em` or `rem` for these. 
* **Media queries**: `em` is good for cross browser support
* You don't really need pixels anymore, but can be used for little things like shadows, borders etc.