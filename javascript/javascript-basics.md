**JavaScript** allows you to change CSS and HTML elements on your website after the site has been loaded, which gives you the ability to make your site more interactive and engaging for users

JS gives you the tools that you need to alter the behavior of different elements that are found on a website page, such as menu interactions (open and close).

This is an example of a very basic program in JavaScript. Similar to a print statement in Python, this will write the text 'Hello World' to the developer console (normally viewed within the web browser by pressing F12).

```js
console.log("Hello World!");
```

In some programming languages, semi colons are used to signify the end of a line or statement. In JavaScript, semicolons are not strictly needed in every case. A newline can imply a semicolon but it does not always. In general it is recommended to put semicolons between statements even if they are separated by newlines to prevent errors.

## Comments
There are two types of comments in JavaScript: one line comments and block comments. 

* One line comments start with two forward slash characters
* Multi-line comments start with a forward slash and asterisk and end with an asterisk and forward slash. 

```js
// This comment occupies a line of its own
alert('Hello');

/* An example with two messages.
This is a multiline comment.
*/

alert('World');

```

## Strict Mode

JavaScript's strict mode is a way to _opt in_ to a restricted variant of JavaScript, thereby implicitly opting-out of "[sloppy mode](https://developer.mozilla.org/en-US/docs/Glossary/Sloppy_mode)".

Strict mode makes several changes to normal JavaScript semantics:

1. Eliminates some JavaScript silent errors by changing them to throw errors.
2. Fixes mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes be made to run faster than identical code that's not strict mode.
3. Prohibits some syntax likely to be defined in future versions of ECMAScript

How to invoke (must be either at the top of the script or the beginning of a function, which makes it local to that function only:
```js
// Whole-script strict mode syntax
"use strict";
const v = "Hi! I'm a strict mode script!";

// Function specific strict mode
function restricted() {
  "use strict";
  restricted.caller; // throws a TypeError
  restricted.arguments; // throws a TypeError
}
```

It's not essential to enable strict mode for most beginner use cases but it is generally fine to include at the top of a script. Once code is moved to classes and modules 'use strict' is no longer needed because it's enabled automatically.

## Variables
Variables are 'named storage' for data. Variables can be initialized and assigned values, which may or may not change over time. 

The statement below declares a variable with the name "message":
```javascript
let message;
```

Now we can put some data into the variable using the assignment operator `=`
```javascript
let message;
message = 'Hello'; // store the string 'Hello' in the variable named message
```

This string is saved into the memory area associated with the variable and can be accessed using the variable name.

```javascript
alert(message); // shows the variable content
```
