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