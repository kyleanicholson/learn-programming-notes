**CSS** (Cascading Style Sheets) is a popular style sheet language that determines how a document created in HTML is styled (colors, font styles, layout and responsive features).

* Primarily used to create static visual effectsm buut can also be used to create simple animations.
	* Can also be used to alter the layout and formatting of a website 

* CSS is made up of various rules - rules are made up of a **selector** and a semi colon separated list of **declarations**, with each declaration being made up of a property:value pair.
![[Pasted image 20220925094048.png]]
**Selectors** are the html elements to which CSS rules apply. Here are a few examples of common selectors:

The **universal selector**, * selects all elements of any type
```css
* {
  color: purple; /* Every element has the color purple applied to it */
}
```

**Type selectors** select all elements of the given element type
```css
div {
  color: white; /* Applies to every div element
}
```

**Class selectors** select all elements of a given class.
(Elements can be assigned multiple classes)
```html
<div class="alert-text">
  Please agree to our terms of service.
</div>
```

```css
.alert-text {
  color: red;
}
```

**ID Selectors** select an element with the given ID. In contrast with classes, elements can only have one ID.
(IDs should be used sparingly, if at all)

```html
<div id="title">My Awesome 90's Page</div>
```

```css
#title {
  background-color: red;
}
```

CSS rules can be applied to multiple classes:
```css
.read,
.unread {
  color: white;
  background-color: black;
}
```

Selectors can be chained as a list without any separation. 
```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

```css
.subsection.header {
  color: red; }/* Selects any element that has both the subsection and header classes */

.subsection#preview {
  color: blue;} /* Selects 
  
```

**Descendant combinators** will cause elements that match the last selector to be selected if they also have an ancestor (parent, grandparent, etc. ) that matches the previous selector. 
```html
<div class="ancestor"> <!-- A -->
  <div class="contents"> <!-- B -->
    <div class="contents"> <!-- C -->
    </div>
  </div>
</div>

<div class="contents"></div> <!-- D -->
```

```css
/* styles.css */

.ancestor .contents {
  /* some declarations */ 
}
```
 In the above example, the first two elements with the `contents` class (B and C) would be selected, but that last element (D) won’t be


**Specificity**
A CSS declaration that is more specific will take precedence over less specific ones.

* An ID selector will always beat any number of class selectors, a class selector will always beat any number of type selectors, and a type selector will always beat any number of anything less specific than it.
* When no declaration has a selector with a higher specificity, a larger amount of a single selector will beat a smaller amount of that same selector.

**Inheritance**
Inheritance refers to certain CSS properties that, when applied to an element, are inherited by that element’s descendants, even if we don’t explicitly write a rule for those descendants. Typography based properties (`color`, `font-size`, `font-family`, etc.) are usually inherited, while most other properties aren’t.

**Rule Order**
The final factor, the end of the line, the tie-breaker of the tie-breaker. Let’s say that after every other factor has been taken into account, there are still multiple conflicting rules targeting an element. How does the cascade determine which rule to apply?

Really simply, actually. Whichever rule was the _last_ defined is the winner.
