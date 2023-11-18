### What is an HTML Table and Why Use It?

HTML tables are a structured way to present data in rows and columns, like a grid. They're essential for displaying tabular data on websites, enabling you to quickly find connections between different types of information. For instance, they can show the relationship between a person and their age, or days of the week with scheduled activities​[](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)

### How Do HTML Tables Work?

Tables rely on a rigid structure, with visually associated row and column headers facilitating easy interpretation of information. [MDN Reference](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)

Example:
```html
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Chris</td>
      <td>38</td>
    </tr>
    <tr>
      <td>Sarah</td>
      <td>29</td>
    </tr>
  </tbody>
</table>

```

Produces the following table
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Chris</td>
      <td>38</td>
    </tr>
    <tr>
      <td>Sarah</td>
      <td>29</td>
    </tr>
  </tbody>
</table>


### Styling HTML Tables

Proper CSS styling enhances the readability and visual appeal of tables. Basic CSS properties like `border`, `padding`, and `border-collapse` can significantly improve the table's look. [MDN Reference](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)

See basic table styling example [here](obsidian://open?vault=learn-programming-notes&file=Web%20Development%2Fsnippets)
### Utilizing Colspan and Rowspan in Tables

`colspan` and `rowspan` attributes allow cells to span multiple columns or rows. `colspan` is used when you want a cell to stretch across several columns, and `rowspan` is used for spanning across multiple rows. These attributes are essential for creating complex table layouts and ensuring that the table accurately represents the data structure.
```html
<table>
  <tr>
    <th rowspan="2">Name</th>
    <th colspan="2">Details</th>
  </tr>
  <tr>
    <td>Age</td>
    <td>Occupation</td>
  </tr>
  <tr>
    <td>Chris</td>
    <td>38</td>
    <td>Developer</td>
  </tr>
</table>
```
<table>
  <tr>
    <th rowspan="2">Name</th>
    <th colspan="2">Details</th>
  </tr>
  <tr>
    <td>Age</td>
    <td>Occupation</td>
  </tr>
  <tr>
    <td>Chris</td>
    <td>38</td>
    <td>Developer</td>
  </tr>
</table>


### Accessibility and HTML Tables

Properly implemented tables are accessible and enhance the experience for both sighted and visually impaired users. [MDN Reference](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)


### Incorporating Colgroup and Col for Column Grouping

`colgroup` and `col` tags in HTML tables are used for grouping and applying styles to entire columns without repeating styles in each cell. The `colgroup` tag wraps around any number of `col` elements, each representing a column.

```html
<table>
  <colgroup>
    <col style="background-color:yellow">
    <col style="background-color:pink">
  </colgroup>
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Chris</td>
    <td>38</td>
  </tr>
  <tr>
    <td>Sarah</td>
    <td>29</td>
  </tr>
</table>
```

<table>
  <colgroup>
    <col style="background-color:yellow">
    <col style="background-color:pink">
  </colgroup>
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Chris</td>
    <td>38</td>
  </tr>
  <tr>
    <td>Sarah</td>
    <td>29</td>
  </tr>
</table>

In this example, the first column (Name) has a yellow background, and the second column (Age) has a pink background, applied through the `col` elements within `colgroup`.

### Table Captions

Table captions contain a description of the table contents and are nested within the table element (just below the opening tag)

```html
<table>
  <caption>
    Dinosaurs in the Jurassic period
  </caption>

  …
</table>

```

### `<thead>, <tfoot>, <tbody>`

- The `<thead>` element must wrap the part of the table that is the header — this is usually the first row containing the column headings, but this is not necessarily always the case. If you are using [`<col>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/col)/[`<colgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup) element, the table header should come just below those.
- The `<tfoot>` element needs to wrap the part of the table that is the footer — this might be a final row with items in the previous rows summed, for example. You can include the table footer right at the bottom of the table as you'd expect, or just below the table header (the browser will still render it at the bottom of the table).
- The `<tbody>` element needs to wrap the other parts of the table content that aren't in the table header or footer. It will appear below the table header or sometimes footer, depending on how you decided to structure it.


### Nested Tables

Tables can be nested within another table

```html
<table id="table1">
  <tr>
    <th>title1</th>
    <th>title2</th>
    <th>title3</th>
  </tr>
  <tr>
    <td id="nested">
      <table id="table2">
        <tr>
          <td>cell1</td>
          <td>cell2</td>
          <td>cell3</td>
        </tr>
      </table>
    </td>
    <td>cell2</td>
    <td>cell3</td>
  </tr>
  <tr>
    <td>cell4</td>
    <td>cell5</td>
    <td>cell6</td>
  </tr>
</table>

```

### The scope attribute

The [`scope`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th#scope) attribute can be added to the `<th>` element to tell screen readers exactly what cells the header is a header for — is it a header for the row it is in, or the column, for example

```html
<thead>
  <tr>
    <th scope="col">Purchase</th>
    <th scope="col">Location</th>
    <th scope="col">Date</th>
    <th scope="col">Evaluation</th>
    <th scope="col">Cost (€)</th>
  </tr>
</thead>

```

An alternative to using the `scope` attribute is to use [`id`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes#id) and [`headers`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td#headers) attributes to create associations between headers and cells. The way they are used is as follows:

1. You add a unique `id` to each `<th>` element.
2. You add a `headers` attribute to each `<td>` element. Each `headers` attribute has to contain a list of the `id`s of all the `<th>` elements that act as a header for that cell, separated by spaces.


```html
<thead>
  <tr>
    <th id="purchase">Purchase</th>
    <th id="location">Location</th>
    <th id="date">Date</th>
    <th id="evaluation">Evaluation</th>
    <th id="cost">Cost (€)</th>
  </tr>
</thead>
<tbody>
  <tr>
    <th id="haircut">Haircut</th>
    <td headers="location haircut">Hairdresser</td>
    <td headers="date haircut">12/09</td>
    <td headers="evaluation haircut">Great idea</td>
    <td headers="cost haircut">30</td>
  </tr>

  …
</tbody>
```

In most cases, `scope` is sufficient and reduces the total amount of markup

