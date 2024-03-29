
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

There are a number of useful 'built-in' input types that can be used to collect different types of information. Here are a few of the most useful ones, with code examples.

Search field
```html
<input type="search" id="search" name="search" /> 
```

Phone
```html
<input type="tel" id="tel" name="tel" />
```

URL
```html
<input type="url" id="url" name="url" />
```

Number
```html
<input type="number" name="age" id="age" min="1" max="10" step="2" />
%% use `step` attribute to set the increment increase and decrease caused by pressing the spinner buttons %%

%% To allow float numbers, specify [`step="any"`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/step) %%
```

Sliders (useful when setting a non-exact range such as home prices)
```html
<label for="price">Choose a maximum house price: </label>
<input
  type="range"
  name="price"
  id="price"
  min="50000"
  max="500000"
  step="100"
  value="250000" />
<output class="price-output" for="price"></output>
```

Date and time pickers
```html
<input type="datetime-local" name="datetime" id="datetime" />
<input type="month" name="month" id="month" />
<input type="time" name="time" id="time" /> 
<input type="week" name="week" id="week" />
%% All date and time controls can be constrained using the [`min`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/min) and [`max`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/max) attributes %%

```

Color picker
```html
<input type="color" name="color" id="color" />
```

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

In general it's best to use the label instead of placeholder to explain a form control, or add an extra HTML element beneath the form control to add an explanation or example.
### **The name attribute**

We also need to let the backend, where we send our data, know what each piece of data represents. We do this by adding a `name` attribute to our inputs:
```
<label for="first_name">First Name:</label>
<input type="text" id="first_name" name="first_name">
```

The `name` attribute serves as a reference to the data inputted into a form control after submitting it. You can think of it as a variable name for the input. Form input should always have a `name` attribute; otherwise, it will be ignored when the form is submitted.

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

### The autocomplete attribute

There are other examples where it can still be hard for browsers to identify the data type solely from the `name`, `id`, and `type` attributes. You can help here by using the `autocomplete`attribute.

```html
 <label for="name">Name</label>
 <input type="text" name="name" id="name" autocomplete="name">
```
If you have entered a name before, the browser will probably offer the option to fill it in.

You can use `autocomplete="email"` for an email field, so users get the autofill option for an email address.

As this is a sign-up form, users shouldn't get the option to fill in previously used passwords. You can use `autocomplete="new-password"` to ensure browsers offer the option to generate a new password.

There are values for the credit card number `cc-number`, credit card expiration date `cc-exp`, and [all other information needed](https://developer.mozilla.org/docs/Web/HTML/Attributes/autocomplete#values) for a credit card payment

Sometimes it's important to directly disable autofill - for example for a one-time code field:
```html
<label for="one-time-code">One-time code</label><input autocomplete="off" type="text" name="one-time-code" id="one-time-code">
```
### The required attribute

The `required` attribute tells the browser that the field is mandatory. The browser also tests if the entered data matches the format of the `type`. The email field shown in the example is only valid if it's not empty and if the entered data is a valid email address.

```html
<label for="name">Name (required)</label>
<input required type="text" id="name" name="name">
```

### The pattern attribute

Sometimes you want to define more advanced validation rules. Again, you can use an HTML attribute. It's called `pattern`, and you can define a [regular expression](https://regex101.com/) as the value.

```html
<label for="animal">What is your favorite animal? (required)</label><input required pattern="[a-z]{2,20}" type="text" id="animal" name="animal">
```

### The inputmode attribute
`inputmode` attribute is supported on [Android and iOS](https://caniuse.com/?search=inputmode). In contrast to the `type` attribute, the `inputmode` attribute only changes the on-screen keyboard provided, not the behavior of the element itself. Using `inputmode` is a good option if you want to keep the default user interface and the default validation rules of an `<input>`
Use `inputmode="numeric"` to get a numeric on-screen keyboard (only for incremental fields)

### Minlength and maxlength attributes
To add the minimum length validation, we give the form control a `minlength` attribute with an integer value that represents the minimum amount of characters we want to allow in the form control:

```html
<form action="#" method="get">
  <div>
    <textarea placeholder="What's happening?" minlength="3" maxlength="20"></textarea>
  </div>
  
  <button type="submit">Tweet</button>
</form>
```

### Min and Max 
To add a minimum value validation, we give the form control a `min` attribute with an integer value which represents the minimum number we want the form control to accept:
```html
<form action="#" method="get">
  <div>
    <label for="quantity">Quantity</label>
  </div>
  <input type="number" id="quantity" name="quantity" min="1" value="0">
  
  <div>
    <button type="submit">Place Order</button>
  </div>
</form>
```

## **Text area**

While technically not an input element, the text area element provides an input box that can accept text that spans multiple lines like user comments and reviews. It can also be resized by clicking and dragging the bottom right corner to make it bigger or smaller. You can disable the resizing, but this is generally considered bad for Ux. Instead, use `resize: vertical` to ensure users can resize vertically but not horizontally.

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
## Select dropdown
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

Multiple choice select boxes are also possible using `multiple` attribute
```html
<select id="multi" name="multi" multiple size="2">
  <optgroup label="fruits">
    <option>Banana</option>
    <option selected>Cherry</option>
    <option>Lemon</option>
  </optgroup>
  <optgroup label="vegetables">
    <option>Carrot</option>
    <option>Eggplant</option>
    <option>Potato</option>
  </optgroup>
</select>

```

## Autocomplete box

You can provide suggested, automatically-completed values for form widgets using the [`<datalist>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/datalist) element with child [`<option>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option) elements to specify the values to display. The `<datalist>` needs to be given an `id`.

The data list is then bound to an [`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input) element (e.g. a `text` or `email` input type) using the [`list`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#list) attribute, the value of which is the `id` of the data list to bind.

Once a data list is affiliated with a form widget, its options are used to auto-complete text entered by the user; typically, this is presented to the user as a drop-down box listing possible matches for what they've typed into the input.

```html
<label for="myFruit">What's your favorite fruit?</label>
<input type="text" name="myFruit" id="myFruit" list="mySuggestion" />
<datalist id="mySuggestion">
  <option>Apple</option>
  <option>Banana</option>
  <option>Blackberry</option>
  <option>Blueberry</option>
  <option>Lemon</option>
  <option>Lychee</option>
  <option>Peach</option>
  <option>Pear</option>
</datalist>

```
## Radio Buttons

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


## Checkboxes

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

## Buttons
The button element creates clickable buttons that the user can interact with to submit forms and trigger other actions.

To create a button, we use the `<button>` element. The content or text we want to have displayed inside the button will go within the opening and closing tags:

```html
<button>Click Me</button>
```

The button element also accepts a `type` attribute that tells the browser which kind of button it is dealing with. There are three types of buttons available to us.

**Submit buttons**
When a submit button is clicked, it will submit the form it is contained within. The `type` attribute has a value of submit by default, i.e. if the `type` is not specified or the value provided is invalid.

```html
<button type="submit">Submit</button>
```


**Reset button**

A reset button clears all the data the user has entered into the form and sets all the inputs in the form back to what they were initially.

To create a reset button, we use the button element with a `type` attribute of “reset”:
```html
<button type="reset">Reset</button>
```

**Generic button**
The third and final button type is simply a generic button that can be used for anything. It’s commonly used with JS for creating interactive UI’s.
To create a generic button, we use the button element with a `type` attribute of “button”:

```html
<button type="button">Click to Toggle</button>
```

**Image button**
An image button can also be created using an [`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input) element with its [`type`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#type) attribute set to the value `image`.

```html
<input type="image" alt="Click me!" src="my-img.png" width="80" height="30" />
```
