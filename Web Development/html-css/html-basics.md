**HTML** (Hyper Text Markup Language) is a language that determines how documents and web pages are displayed in a web browser, the language for the building blocks of any website.
- Forms the basic structure of a website
- Almost all elements on an HTML page are just pieces of content wrapped in opening and closing HTML tags
	- HTML elements are containers for content - opening and closing tags tell the browser what content the element contains.
		- The browser can then use that information to determine how it should interpret and format the content.

**HTML tags look like this**:
```
<opening tag> [Content] <closing tag>
```

**Nesting**
* When one element is nested inside another, this forms a parent - child relationship
* Elements at the same level of nesting are considered siblings.
To trigger the boilerplate shortcut in VS Code, type `!` on the first line and press enter.
We use indentation to make the level of nesting clear and readable for ourselves and other developers who will work with our HTML in the future. It is recommended to indent any child elements by two spaces.

**Specific elements to remember**
<!DOCTYPE html> The doctype’s purpose is to tell the browser what version of HTML it should use to render the document.

<html>: root element of the document, meaning that every other element in the document will be a descendant of it

 <head>: element is where we put important meta-information about our webpages, and stuff required for our webpages to render correctly in the browse
 
 <title>: element is used to give webpages a human-readable title which is displayed in our webpage’s browser tab
 
<Div> is a block-level element by default. It is commonly used as a container element to group other elements. Divs allow us to _divide_ the page into different blocks and apply styling to those blocks.

<Span> is an inline-level element by default. It can be used to group text content and inline HTML elements for styling and should only be used when no other semantic HTML element is appropriate.

<body>: Where all the content displayed to end users will go

<h1> to <h6>: Headings (h1 is most important, h6 is least)

<strong>: Makes an element bold and marks it as semantically important.

<em>: Italics / semantic emphasis 

<a> : anchor tag - used for links
<img>: Tag used for images
src attribute contains link to image 
alt = text to display if image does not render / for visually impaired users.

Links to pages on other websites on the internet are called absolute links
Links to other pages within our own website are called relative links

Unordered lists are created using the <ul> element, and each item within the list is created using the list item element <li>
```html
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```
If you instead want to create a list of items where the order _does_ matter, like step-by-step instructions for a recipe, or your top 10 favorite TV shows, then you can use an ordered list.
```html
<ol>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ol>
```



