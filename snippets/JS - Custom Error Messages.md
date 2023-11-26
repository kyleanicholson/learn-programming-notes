```
const nameInput = document.querySelector('[name="name"]');nameInput.addEventListener('invalid', () => {    nameInput.setCustomValidity('Please enter your name.'); });
```

[`setCustomValidity()`](https://developer.mozilla.org/docs/Web/API/HTMLObjectElement/setCustomValidity) method of the Constraint Validation API

Allows you to show the same error messages to everyone (across browsers)