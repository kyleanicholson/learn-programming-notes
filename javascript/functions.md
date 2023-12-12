
## Function Declarations
Functions in JavaScript are one of the core building blocks of the language, allowing you to encapsulate code to perform specific tasks.

```Javascript
function greet(name) { 
	return `Hello, ${name}!`; 
	} 
	console.log(greet("Alice")); // Output: Hello, Alice!
```

## Function Expressions
A function expression can be stored in a variable. The function can be anonymous (without a name).
```js
const square = function(number) {
	return number * number; 
	}; 
	console.log(square(4)); // Output: 16
```

### Arrow Functions
Introduced in ES6, arrow functions provide a concise syntax for writing function expressions. They are particularly useful for inline functions and callbacks.

The syntax for arrow functions is
```js
const functionName = (parameters) => {
  // Code to be executed
};

```

An example of an arrow function:
```js
const add = (a, b) => a + b;

console.log(add(5, 3)); // Output: 8

```


### Scope
The word “scoping” essentially asks, “Where is a certain variable available to me?” - it indicates the current context of a variable. When a variable is not declared within **any** functions, existing outside any `{ curly braces }`, they are said to be in the **global scope**, meaning that they are available everywhere. If they are within a function or `{ curly braces }`, they are known to be **locally scoped**.

Before ECMAScript 6, JavaScript had a single keyword to declare a variable, `var`. These variables can be redefined and updated, and are said to be defined within the **function scope**, meaning, they are only available within the function they are declared in.

In ECMAScript 6, the keywords `let` and `const` were introduced. While `var` variables were function scoped, these allow you to define variables that are **block scoped** - basically, scoping the variable to only be available within the closest set of `{ curly braces }` in which it was defined. These braces can be those of a `for` loop, `if-else` condition, or any other similar construct, and are called, a block. 

### Closures

Functions in JavaScript form closures. A closure refers to the combination of a function and the **surrounding state** within which a function was declared in. This surrounding state, also called its lexical environment, consists of any local variables that were in scope at the time the closure was made. 

```javascript
function makeAdding (firstNumber) {
  // "first" is scoped within the makeAdding function
  const first = firstNumber;
  return function resulting (secondNumber) {
    // "second" is scoped within the resulting function
    const second = secondNumber;
    return first + second;
  }
}
// but we've not seen an example of a "function"
// being returned, thus far - how do we use it?

const add5 = makeAdding(5);
console.log(add5(2)) // logs 7
```

Here, `add5` is a reference to the `resulting` function, created when the `makeAdding` function is executed, thus it has access to the lexical environment of the `resulting` function, which contains the `first` variable, making it available for use, rather than removing it from memory for being out of scope.

## Factory Functions

These fancy-sounding functions work very similar to how constructors did, but with one key difference - they levy the power of closures. Instead of using the `new` keyword to create an object, factory functions simply set up and return the new object when you call the function. They do not use the prototype, which incurs a performance penalty - but as a general rule, this penalty isn’t significant unless you’re creating thousands of objects. Let’s take a basic example to compare them to constructor functions.

```javascript
const User = function (name) {
  this.name = name;
  this.discordName = "@" + name;
}
// hey, this is a constructor - 
// then this can be refactored into a factory!

function createUser (name) {
  const discordName = "@" + name;
  return { name, discordName };
}
// and that's very similar, except since it's just a function,
// we don't need a new keyword
```