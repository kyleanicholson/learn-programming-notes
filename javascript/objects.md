One of the simplest ways you can begin to organize your code is by simply grouping things into objects. In JavaScript, an object is a collection of properties, and a property is an association between a name (or key) and a value. A value of a property can be a function, which is then considered a method of the object.

### Create an object constructor

```js
function Book(title, author, pages, read){
  this.title = title;
  this.author = author;
  this.pages = pages;
  this.read = read;
  this.info = function(){
    console.log(`${this.title} by ${this.author}, ${this.pages} pages, ${this.read ? 'read' : 'not read'}`);
  }
};
```

### Instantiate an object
```js
let lotr = new Book('Lord of the Rings', 'J.R.R. Tolkien', '295', true)

```

### Prototypes 

All objects in JavaScript have a `prototype`. Stated simply, the `prototype` is another object that the original object _inherits_ from, which is to say, the original object has access to all of its `prototype`’s methods and properties. We can define properties and functions common among all objects on the `prototype` to save memory.

 You can check the object’s `prototype` by using the [`Object.getPrototypeOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf) function on the object, like `Object.getPrototypeOf(player1)`. 
 
1. Every `prototype` object inherits from `Object.prototype` by default.
2. An object’s `Object.getPrototypeOf()` value can only be _one_ unique `prototype` object.

It is a common practice in JavaScript to define methods on the prototype for increased efficiency and code readability:
```js
function Student(name, grade) {

this.name = name

this.grade = grade

}

Student.prototype.sayName = function() {

console.log(this.name)

}

Student.prototype.goToProm = function() {

console.log("Eh.. go to prom?")

}
```

You can use `Object.create` to create a new object which inherits from an existing prototype. For example:
```js
function Student() {

} 

Student.prototype.sayName = function() {

console.log(this.name)

}


EighthGrader.prototype = Object.create(Student.prototype)


function EighthGrader(name) {

this.name = name

this.grade = 8

}
```

We can use the [`call()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call) method to copy over properties from one constructor into another constructor.
```js
// Initialize a constructor function for a new Hero
function Hero(name, level) {
  this.name = name;
  this.level = level;
}
...
// Add greet method to the Hero prototype
Hero.prototype.greet = function () {
  return `${this.name} says hello.`;
}

...
// Initialize Warrior constructor
function Warrior(name, level, weapon) {
  // Chain constructor with call
  Hero.call(this, name, level);

  // Add a new property
  this.weapon = weapon;
}

// Initialize Healer constructor
function Healer(name, level, spell) {
  Hero.call(this, name, level);

  this.spell = spell;
}
```

Prototype properties and methods are not automatically linked when you use `call()` to chain constructors. You can use `Object.setPrototypeOf()` to link the properties in the `Hero` constructor to the `Warrior` and `Healer` constructors, making sure to put it before any additional methods.


### Object Shorthand Notation

In 2015, a shortcut to creating objects was added to JavaScript. Say we wanted to make an object with a name, age, and color. We’d write it as the following:

```javascript
const name = "Bob";
const age = 28;
const color = "red";

const thatObject = { name: name, age: age, color: color };
```

However, now, if we have a variable with the same name as that of the property to which we are assigning it, we can simply write it once!

```javascript
const nowFancyObject = { name, age, color };
```

An added advantage to this is that it’s now possible to console.log values neatly!

```javascript
// If you wanted to log these values, earlier,
// you would have done the following
console.log(name, age, color);
// which would have resulted in a mess - Bob 28 red

// Try wrapping it in some { curly braces } now,
// which makes it an object!
console.log({ name, age, color });
// now it logs as - { name: "Bob", age: 28, color: "red" }
```


### Destructuring
When you have an object, you can extract a property of an object into a variable of the same name, or any named variable for an array. Take a look at the example below:

```javascript
const obj = { a: 1, b: 2 };
const { a, b } = obj;
// This creates two variables, a and b,
// which are equivalent to
// const a = obj.a;
// const b = obj.b;

const array = [1, 2, 3, 4, 5];
const [ zerothEle, firstEle ] = array;
// This creates zerothEle and firstEle, both of which point
// to the elements in the 0th and 1st indices of the array
```


## Private variables in functions

Notice that the object we return in the factory function does not contain the `reputation` variable itself, nor any copy of its value. Instead, the returned object contains two functions - one that reads the value of the `reputation` variable, and another that increases its value by one. The `reputation` variable is what we call a “private” variable, since we cannot access the variable directly in the object instance - it can only be accessed via the closures we defined.

```javascript
function createUser (name) {
  const discordName = "@" + name;

  let reputation = 0;
  const getReputation = () => reputation;
  const giveReputation = () => reputation++;

  return { name, discordName, getReputation, giveReputation };
}

const josh = createUser("josh");
josh.giveReputation();
josh.giveReputation();

console.log({
  discordName: josh.discordName,
  reputation: josh.getReputation()
});
// logs { discordName: "@josh", reputation: 2 }
```

A private variable or function uses closures to create smaller, dedicated variables and functions within a factory function itself - things that we do not _need_ to return in the object itself. This way we can create neater code, without polluting the returned object with unnecessary variables that we create while creating the object itself.

### Prototypal inheritance with factories
We can give our objects access to the properties of another in the context of factories (similar to object / prototype inheritance). We need to extend the `User` factory into a `Player` factory that needs to control some more metrics - there are some ways to do that
```javascript
function createPlayer (name, level) {
  const { discordName, getReputation } = createUser(name);

  const increaseLevel = () => level++;
  return { name, discordName, getReputation, increaseLevel };
}
```