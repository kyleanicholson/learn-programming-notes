## What Are SVGs?

SVG stands for **Scalable Vector Graphics**. They are images defined by mathematical formulas, not pixels, so they can scale without losing quality. SVGs are written in XML, a markup language similar to HTML.

## What are the uses of SVGs?
- Ideal for web icons, charts, and simple images.
- They can be styled and animated with CSS and JavaScript.
- They are not ideal for complex, detailed images like photographs

## How can you add SVGs to your website?

Method 1: Linked (like regular images)
```html
<img src="path/to/your-image.svg" alt="Description">
```

Method 2: Inline (directly in HTML)
```html
<!--- An SVG of a CIRCLE  --->
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
</svg>
```

Inline SVGs are part of the HTML and can be styled or scripted.

### Is it better to use linked or inline?

It doesn't really matter. Inline can be manipulated more easily through CSS, JS, but it causes the code to be bloated. Linking is a little cleaner so when in doubt just go with a link.