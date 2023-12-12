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
