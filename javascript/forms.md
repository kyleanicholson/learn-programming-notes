You can use JavaScript to reveal an input only when the associated `<input>` is selected.

For example:

```js
if(event.target.checked) {
// show additional field}
else{
// hide additional field
}
```

*  Ensure users can submit a form without leaving a page
Imagine you have a comment form. When a reader adds a comment and submits the form, it would be ideal if they could immediately see the comment without a page refresh.

To achieve this, listen to the `onsubmit` event, then use `event.preventDefault()` to prevent the default behavior, and send the `FormData` using the [Fetch API](https://developer.mozilla.org/docs/Web/API/Fetch_API). Your backend script can check if a `POST` request appears to be from the browser (using the `action` attribute of a form element, where `method="post"`) or from JavaScript, such as a `fetch()` request.

```js
if (req.xhr || req.headers.accept.indexOf('json') !== -1) {    // return JSON} else {    // return HTML}
```

You can make sure the same message is shown to all users, and that the message aligns with your site's [style and tone](https://developers.google.com/style/tone)? Use the [`setCustomValidity()`](https://developer.mozilla.org/docs/Web/API/HTMLObjectElement/setCustomValidity) method of the [Constraint Validation API](https://developer.mozilla.org/docs/Web/API/Constraint_validation) to define your own error messages.

```js
const usernameInput = document.querySelector('[name="name"]'); 

usernameInput.addEventListener('invalid', () => {  
  usernameInput.setCustomValidity('Please enter your name.');
});
```

You can also listen for the [`blur`](https://developer.mozilla.org/docs/Web/API/Element/blur_event) event which fires when an element loses focus, and use the [`ValidityState`](https://developer.mozilla.org/docs/Web/API/ValidityState) interface to detect if a form control is invalid.

To notify screen reader users if the password is currently shown or hidden, use a hidden element with `aria-live="polite"`, and change its text accordingly. It's important to enable screen reader users to know when a password is displayed and visible to someone else looking at their screen.

```
<span class="visually-hidden" aria-live="polite">    <!-- Dynamically change this text with JavaScript --></span>
```