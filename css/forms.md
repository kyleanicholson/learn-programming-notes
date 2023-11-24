**Forms** are one of the most critical parts of any website. They are a user's gateway into the website's back end - the user provides data in a form, and the website does stuff with it. 

Each form input needs to have the proper type of input since there are often multiple ways to collect data, but there is only one 'easiest' way for the user. 

## Form action and method

The `form` element is a container element that wraps all of the inputs a user will interact with on a form. 

The form element accepts two essential attributes; the first is the `action` attribute which takes a URL value that tells the form where it should send its data to be processed. Later in the curriculum, we will learn to hook backend systems up to frontend forms using this attribute.

The second is the `method` attribute which tells the browser [which HTTP request method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) it should use to submit the form. The GET and POST request methods are the two you will find yourself using the most. We use GET when we want to retrieve something from a server. For example, Google uses a GET request when you search as it _gets_ the search results.

POST is used when we want to change something on the server, for example, when a user makes an account or makes a payment on a website.

Example form element:
```html
<form action="example.com/path" method="post">

</form>
```

## Form Controls

Form controls allow us to collect user data - text boxes, dropdowns, checkboxes, and buttons are all examples of form controls.

### The input element

The input element is the most versatile of all form control elements-- it accepts a type attribute which tells the browser what type of data it should expect and how it should render the input element.

Example of a text input:
```html
<form action="example.com/path" method="post">
  <input type="text">
</form>
```

Text inputs accept any text input. For example, you would use it to collect things like users’ first and last names.

### Labels

We can give our inputs a label to inform users what type of data they are expected to enter. To create a label, we use the `<label>` element. The text we want displayed in the label will go between its opening and closing tags:

```html
<form action="example.com/path" method="post">
  <label for="first_name">First Name:</label>
  <input type="text" id="first_name">
</form>
```

Labels accept a `for` attribute, which associates it with a particular input. The input we want to associate with a label needs an `id` attribute with the same value as the label’s `for` attribute. When a label is associated with an input and is clicked, it will focus the cursor on that input, ready for the user to input some data.


### Placeholder attribute

To guide users on what to enter in form elements, we can include placeholder text in input fields.

```html
<label for="first_name">First Name:</label>
<input type="text" id="first_name" placeholder="Bob...">
```

### **The name attribute**

We also need to let the backend, where we send our data, know what each piece of data represents. We do this by adding a `name` attribute to our inputs:
```
<label for="first_name">First Name:</label>
<input type="text" id="first_name" name="first_name">
```

The `name` attribute serves as a reference to the data inputted into a form control after submitting it. You can think of it as a variable name for the input. Form input should always have a `name` attribute; otherwise, it will be ignored when the form is submitted.

### **Using form controls outside of forms**

You can use any of the form controls HTML provides outside of the `<form>` element, even when you don’t have a backend server where you can send data.

For example you might want to have an input that gets some data from a user and display that somewhere else on the page with JavaScript.


### **The type attribute**

`Email inputs` are specialized text inputs just for email addresses. They are different from text inputs in that they will display a different keyboard which will include the @ symbol on mobile devices to make entering email addresses easier.

```html
<label for="user_email">Email Address:</label>
<input type="email" id="user_email" name="email" placeholder="you@example.com">
```

`Password inputs` are another specialized text input. They differ from regular text inputs in that they mask the inputted data with another character – usually an asterisk (*) or bullet point (•) – to prevent anyone from seeing what has been entered.

```html
<label for="user_password">Password:</label>
<input type="password" id="user_password" name="password">
```

The `number input` only accepts number values and ignores any other characters the user tries to enter.

```html
<label for="amount">Amount:</label>
<input type="number" id="amount" name="amount">
```

To collect dates from a user, we can use a `date input`. This input is unique because it provides a better user experience for choosing dates by rendering a simple date picker calendar.

```html
<label for="dob">Date of Birth:</label>
<input type="date" id="dob" name="dob">
```

### **Text area**

While technically not an input element, the text area element provides an input box that can accept text that spans multiple lines like user comments and reviews. It can also be resized by clicking and dragging the bottom right corner to make it bigger or smaller.

To create a text area, we use the `<textarea>` element *closing tag required*:

```html
<textarea></textarea>
```

You can place content inside the textarea if you want the field to have initial content. 
```html
<textarea>Some initial content</textarea>
```

`rows` and `cols` attributes allow you to control the initial height (rows) and width (cols) of the text area:
```html
<textarea rows="20" cols="60"></textarea>
```


### Select dropdown
The select element renders a dropdown list where users can select an option. Syntactically, select elements have similar markup to unordered lists. The select element wraps option elements which are the options that can be selected.

```html
<select name="Car">
  <option value="mercedes">Mercedes</option>
  <option value="tesla">Tesla</option>
  <option value="volvo">Volvo</option>
  <option value="bmw">BMW</option>
  <option value="mini">Mini</option>
  <option value="ford">Ford</option>
</select>
```

All the option elements should have a `value` attribute (otherwise the text content inside is used). This value will be sent to the server when the form is submitted.

We can set one of the options to be the default selected element when the browser first renders the form by giving one of the options the `selected` attribute:

```html
<select name="Car">
  <option value="mercedes">Mercedes</option>
  <option value="tesla">Tesla</option>
  <option value="volvo" selected>Volvo</option>
  <option value="bmw">BMW</option>
  <option value="mini">Mini</option>
  <option value="ford">Ford</option>
</select>
```
We may also split the list of options into groups using the `<optgroup>` element. The optgroup element takes a `label` attribute which the browser uses as the label for each group:
```html
<select name="fashion">
  <optgroup label="Clothing">
    <option value="t_shirt">T-Shirts</option>
    <option value="sweater">Sweaters</option>
    <option value="coats">Coats</option>
  </optgroup>
  <optgroup label="Foot Wear">
    <option value="sneakers">Sneakers</option>
    <option value="boots">Boots</option>
    <option value="sandals">Sandals</option>
  </optgroup>
</select>
```

### Radio Buttons

Select dropdowns are great for saving space on the page when we have an extensive list of options we want users to choose from. However, when we have a smaller list of 5 or fewer options to choose from, it is often a better user experience to have them displayed on the page instead of hidden behind a dropdown. Radio buttons allow us to create multiple options that the user can choose one of. To create radio buttons, we use the ever adaptable input element again with a `type` attribute of “radio”:

```html
<h1>Ticket Type</h1>
<div>
  <input type="radio" id="child" name="ticket_type" value="child">
  <label for="child">Child</label>
</div>

<div>
  <input type="radio" id="adult" name="ticket_type" value="adult">
  <label for="adult">Adult</label>
</div>

<div>
  <input type="radio" id="senior" name="ticket_type" value="senior">
  <label for="senior">Senior</label>
</div>
```

We can set the default selected radio button by adding the `checked` attribute to it:

```html
<h1>Ticket Type</h1>
<div>
  <input type="radio" id="child" name="ticket_type" value="child">
  <label for="child">Child</label>
</div>

<div>
  <input type="radio" id="adult" name="ticket_type" value="adult" checked>
  <label for="adult">Adult</label>
</div>

<div>
  <input type="radio" id="senior" name="ticket_type" value="senior">
  <label for="senior">Senior</label>
</div>
```


**Checkboxes**

Checkboxes are similar to radio buttons in that they allow users to choose from a set of predefined options. But unlike radio buttons, they allow multiple options to be selected at once.

To create a checkbox, we use the input element with a `type` attribute of “checkbox”:

```html
<h1>Pizza Toppings</h1>

<div>
  <input type="checkbox" id="sausage" name="topping" value="sausage">
  <label for="sausage">Sausage</label>
</div>

<div>
  <input type="checkbox" id="onions" name="topping" value="onions">
  <label for="onions">Onions</label>
</div>

<div>
  <input type="checkbox" id="pepperoni" name="topping" value="pepperoni">
  <label for="pepperoni">Pepperoni</label>
</div>

<div>
  <input type="checkbox" id="mushrooms" name="topping" value="mushrooms">
  <label for="mushrooms">Mushrooms</label>
</div>
```

We can also have a single checkbox when we want users to toggle if they want something to be true or false. Like signing up to a newsletter when they create an account for example:

```html
<div>
  <input type="checkbox" id="newsletter" name="news_letter">
  <label for="newsletter">Send me the news letter</label>
</div>
```

We can set checkboxes to be checked by default on page load by giving them a `checked` attribute:

```html
<div>
  <input type="checkbox" id="newsletter" name="news_letter" checked>
  <label for="newsletter">Send me the news letter</label>
</div>
```