**The Box Model**
Every single thing on a webpage is a rectangular box.

![[Pasted image 20221001183145.png]]

### Block vs Inline
* Default style for most elements is 'display:block'
* By default **block** elements appear on the page stacked atop each other, each new element starting on a new line.
* **Inline** elements do not start on a new line - they appear in line with whatever 
* Examples of thes are a and span.

* By default, a block level element's content fills the available inline space of the parent element containing it and grows along the block dimension to accommodate its content. 
* The size of Inline elements is just the size of their content. You can't set width or height on inline elements — they just sit inside the content of block level elements
 * ***Inline-block** *allows to set a width and height on the element -* Margins are respected with inline-block elements

### Flexbox
* Default way of positioning elements for many developers
* Toolbox of properties that you can use to put things where you need them.
	* Some of these properties belong on the _flex container_, while some go on the _flex items_.
![[Pasted image 20221011204201.png]]

* Creating and nesting multiple flex containers and items is the primary way we will be building up complex layouts

#### Flex Properties
* 'Flex' declaration is shorthand for 3 properties that you can set on a flex item.
	* These properties affect how flex items size themselves within their container.


