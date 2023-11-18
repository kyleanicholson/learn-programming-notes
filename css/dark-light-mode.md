# How to implement color themes
## General ideas
- CSS variables can point to other variables.
- You can't just invert the colors
- For light and dark you can use media queries 'prefers theme'
- Drop shadows do not look good on white
- 1px border around content helps separate content 
- Avoid flash of unthemed content -> may need to use a cookie to avoid

## Create global CSS variables
### Color variables
- You can use hue OKLCH colors to create multiple hues from light to dark (entire color palette).
-- Do this for the main colors of your palette.

### Typography
- body font family, heading font family
- shadows, shadow color, 

### Primary, Accent, Background variables
- Define colors 

## Component Level Variables

- You can override global CSS variables at the component level.

## Opacity values
- Color mixes for a cross browser solution?


