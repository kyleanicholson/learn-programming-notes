Most form widgets can be styled using standard CSS styling techniques. There are also special selectors - [UI pseudo-classes](https://developer.mozilla.org/en-US/docs/Learn/Forms/UI_pseudo-classes) - that enable styling based on the current UI state.


## Fonts and Text
CSS font and text features can be used with any widget, however, some widgets may not inherit `font-family` and `font-size` from their parents (certain browsers). To make a form's appearance consistent with the the rest of the content, you can add these rules to your stylesheet:

```css
button,
input,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
}
```

The [`inherit`](https://developer.mozilla.org/en-US/docs/Web/CSS/inherit) property value causes the property value to match the computed value of the property of its parent element; inheriting the value of the parent.

## Box sizing
**Each widget has its own rules for border, padding, and margin.** To give the same size to several different widgets, you can use the [`box-sizing`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) property along with some consistent values for other properties:

```css
input,
textarea,
select,
button {
  width: 150px;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
****
```


## Legend Placement

By default, legend is always positioned over the top border of its [`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) parent, near the top left corner. To position it somewhere else, for example inside the fieldset somewhere, or near the bottom left corner, you need to rely on the positioning.

```css
fieldset {
  position: relative;
}

legend {
  position: absolute;
  bottom: 0;
  right: 0;
}
```

The `<fieldset>` needs to be positioned too, so that the `<legend>` is positioned relative to it (otherwise the `<legend>` would be positioned relative to the `<body>`).