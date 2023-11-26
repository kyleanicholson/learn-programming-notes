**Forms** are one of the most critical parts of any website. They are a user's gateway into the website's back end - the user provides data in a form, and the website does stuff with it.  Forms are also used on the client-side to immediately update the interface in some way (for example, add another item to a list, or show or hide a UI feature).

Each form input needs to have the proper type of input since there are often multiple ways to collect data, but there is only one 'easiest' way for the user. 

From a user experience (UX) point of view, it's important to remember that the bigger your form, the more you risk frustrating people and losing users. Keep it simple and stay focused: ask only for the data you absolutely need.

**Forms can make a website usable** or unusable, because they stand in the way of the user achieving their goal;

**Forms need to be usable** in order to help the user achieve that goal.

## Form action and method

The `form` element is a container element that wraps all of the inputs a user will interact with on a form.  When a form is submitted (for example, when the user clicks the **Submit** button), the browser makes a request. A script can respond to that request and process the data. By default, the request is made to the page where the form is shown.

The form element accepts two essential attributes; the first is the `action` attribute which takes a URL value that tells the form where it should send its data to be processed. Later in the curriculum, we will learn to hook backend systems up to frontend forms using this attribute.

The second is the `method` attribute which tells the browser [which HTTP request method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) it should use to submit the form. The GET and POST request methods are the two you will find yourself using the most. We use GET when we want to retrieve something from a server. For example, Google uses a GET request when you search as it _gets_ the search results.

POST is used when we want to change something on the server, for example, when a user makes an account or makes a payment on a website. For forms that process sensitive data use the `POST` method. The data is encrypted (if you use HTTPS) and only accessible by the backend script that processes the request. The data is not visible in the URL. A common example is a sign-in form.

Example form element:
```html
<form action="example.com/path" method="post">

</form>
```

*Note*: *You can use any of the form controls HTML provides outside of the `<form>` element, even when you don’t have a backend server where you can send data*. *For example you might want to have an input that gets some data from a user and display that somewhere else on the page with JavaScript.*


### Organizing form elements

In larger forms, users can easily get overwhelmed and discouraged if there are many inputs to fill in.  HTML provides a couple of elements that make it easy to organize forms into sections that are visually distinct and manageable to digest.

**Fieldset element** 
The fieldset element is a container element that allows us to group related form inputs into one logical unit. To create a fieldset, we use the `<fieldset>` element. Whatever form inputs we want to group together go within the opening and closing fieldset tags:

```html
<fieldset>
  <label for="first_name">First Name</label>
  <input type="text" id="first_name" name="first_name">

  <label for="last_name">Last Name</label>
  <input type="text" id="last_name" name="last_name">
</fieldset>
```

**Legend**
The legend element is used to give field sets a heading or caption so the user can see what a grouping of inputs is for.

To create a legend, we use the `<legend>` element with the text we want to display within its opening and closing tags. A legend should always come right after an opening fieldset tag:
```html
<fieldset>
  <legend>Contact Details</legend>

  <label for="name">Name:</label>
  <input type="text" id="name" name="name">

  <label for="phone_number">Phone Number:</label>
  <input type="tel" id="phone_number" name="phone_number">

  <label for="email">Email:</label>
  <input type="email" id="email" name="email">
</fieldset>

<fieldset>
  <legend>Delivery Details</legend>

  <label for="street_address">Street Address:</label>
  <input type="text" id="street_address" name="street_address">

  <label for="city">City:</label>
  <input type="text" id="city" name="city">

  <label for="zip_code">Zip Code:</label>
  <input type="text" id="zip_code" name="zip_code">
</fieldset>
```

A common use-case for these elements is using a fieldset to group radio buttons and using a legend to communicate to the user what each of the options is ultimately for:
```html
<fieldset>
  <legend>What would you like to drink?</legend>

  <div>
    <input type="radio" name="drink" id="coffee" value="coffee">
    <label for="coffee">Coffee</label>
  </div>

  <div>
    <input type="radio" name="drink" id="tea" value="tea">
    <label for="tea">Tea</label>
  </div>

  <div>
    <input type="radio" name="drink" id="soda" value="soda">
    <label for="soda">Soda</label>
  </div>
</fieldset>
```

**Meters and Progress Bars**

Meters and progress bars are visual representations of numeric values. Support for [`<progress>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress) and [`<meter>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meter) is available in all modern browsers.

A meter bar represents a fixed value in a range delimited by [`max`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meter#max) and [`min`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meter#min) values. This value is visually rendered as a bar, and to know how this bar looks, we compare the value to some other set values:
```html
<meter min="0" max="100" value="75" low="33" high="66" optimum="0">75</meter>
```

A progress bar represents a value that changes over time up to a maximum value specified by the [`max`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress#max) attribute. Such a bar is created using a [`<progress>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress) element.

```html
<progress max="100" value="75">75/100</progress>

```




