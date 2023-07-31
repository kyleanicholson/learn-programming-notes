Every react application is built on the foundation of React components. 

Within the project directory, open the file *src/App.jsx*. There is some boilerplate code which can mostly be kept, but you can modify the return statement to print a simple Hello World when the application is run. 
```jsx
import { useState } from 'react'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <h1>Hello React</h1>
    </div>
  )
}

export default App

```

Start your application with `npm run dev` and you should see the headline "Hello React".

So what is actually going on here?

The "App" component is a modern React functional component, written as a JavaScript function that must start with a capital letter to be recognized as a React component. 

Within this App component, the line of code `const [count, setCount] = useState(0)` is used to create a state variable called `count`, starting at `0`. 
- **`count`:** A variable that holds a number, initially `0`.
- **`setCount`:** A function to change the value of `count`.
- **`useState`:** A hook imported from React (`import { useState } from 'react'`) that helps manage values that can change over time, allowing you to add state to functional components.

This state management system enables `count` to act as a changing number in your program, with `setCount` as the way to modify that number. When `count` changes, any part of the component using it will automatically update to reflect the new value.

The App component doesn't use any "props" (parameters) in this instance, though props generally enable components to share information with each other.

The component's return code employs JSX syntax, combining JavaScript and HTML to produce dynamic, interactive content in the browser. The appearance of the component is defined by importing a CSS file (`import './App.css'`), which applies styling rules from the same directory's `App.css`.

The function of a component runs every time a component is displayed in the browser. This happens for the initial rendering but also whenever the component updates because it has to display something different due to changes.

For now I am going to remove the code for the useState and count, setCount variables to simplify the code and add a title to our example 'Workout Tracker'. The title is declared as a const variable outside the app function but can be referenced within the function and displayed in the browser using the JSX syntax `{}`

```jsx
import './App.css'

const title = 'Workout Tracker'

function App() {

  return (
    <div>
      <h1>Welcome to {title}</h1>
    </div>
  )
}

export default App

```

Changing this variable in the source code and seeing the change reflected in the browser is related to React and the development server - when the file changes the development server notices and reloads all affected files for the browser. This bridge between React and the development server is called **React Fast Refresh**

Let's add an input to our app. 

```jsx
import './App.css'

const title = 'Workout Tracker'

function App() {

  return (
    <div>
      <h1>Welcome to {title}</h1>
      <label htmlFor="exercise-search">Exercise: </label>
      <input id="exercise-search" type="text" />
    </div>
  )
}

export default App
```

In React's JSX, the `htmlFor` attribute is used instead of the standard HTML `for` attribute. This change is made to avoid confusion with JavaScript's reserved `for` keyword, used in `for` loops. React translates attributes like `htmlFor` back to their native HTML equivalents (`for`) during the rendering process, along with other replacements like using `className` instead of `class`.

You can access the properties within the curly braces using dot notation:

```JSX
import './App.css'

const welcome = {
  greeting: 'Welcome to',
  title: 'The Workout Tracker',
}

function App() {

  return (
    <div>
      <h1>
        {welcome.greeting} {welcome.title}
      </h1>
      <label htmlFor="exercise-search">Exercise: </label>
      <input id="exercise-search" type="text" />
    </div>
  )
}

export default App
```

Or you can define a function and execute it within the curly braces:
```jsx
import './App.css'


function getTitle(title) {
  return title
}

function App() {

  return (
    <div>
      <h1>
        Welcome to {getTitle('The Workout Tracker')}
      </h1>
      <label htmlFor="exercise-search">Exercise: </label>
      <input id="exercise-search" type="text" />
    </div>
  )
}

export default App
```

JSX is a syntax extension to JavaScript - However, browsers don't understand JSX directly. So, before the code reaches the browser, it needs to be converted into regular JavaScript that browsers can run. This conversion is done using tools like Babel. 

For example:
```jsx
const title = 'React'

// JSX
const myElement = <h1>Hello {title}</h1>

// ... gets transpiled to the following js
const myElement = React.createElement('h1', null, `Hello ${title}`);

// ... gets rendered as HTML by React
<h1> Hello React </h1>

```

## Lists

When working with data in JavaScript, most often the data comes as an array of objects. It's therefore important to learn how to render a list of items in React. The `map()` array method in JavaScript is used to iterate over each item in a list in order to return a new version of each item. 

```js
const numbers = [1, 2, 3, 4, 5]

const exponentialNumbers = numbers.map((number) => number ** 2)

console.log(exponentialNumbers)
// [1, 4, 9, 16, 25]
```

In React, the `map()` method is used to transform a list of items into JSX by returning JSX for each item. 

```jsx
const exercise_list = [
  {
    exercise: 'Bench Press',
    sets: 3,
    reps: 10,
    weight: 135,
    objectID: 0,
  },
  {
    exercise: 'Squats',
    sets: 4,
    reps: 8,
    weight: 185,
    objectID: 1,
  },
  {
    exercise: 'Deadlift',
    sets: 2,
    reps: 5,
    weight: 225,
    objectID: 2,
  },
];
```

We can render this list inline in JSX with the array's built in `map()` method:
```jsx

function App() {
  return (
    <div>
      <h1>
        Welcome to {getTitle('The Workout Tracker')}!
      </h1>
      <hr />
      <ul>
        {exercise_list.map(function(exercise) {
          return (
            <li key={exercise.objectID}>
              {exercise.exercise}: {exercise.sets} sets of {exercise.reps} reps, {exercise.weight} lbs
            </li>
          );
        })}
      </ul>
    </div>
  )
}

export default App;
```

This causes our exercise list to display correctly by accessing the properties of each exercise in the list and mapping them to HTML elements. The `key` is used to give each element a stable identifier. Whenever React has to re-render a list it checks whether an item has changed. Keys allow React to efficiently exchange the changed items.

If you do not have a stable identifier, you can use the index of the item in the list, but this is better left as a last resort.

## Adding Components

As a React app grows, there are an increasing number of components to manage. Each component encapsulates or abstracts a meaningful task while contributing to the overall project goals.

In our example fitness app, for example, we may want to abstract the process of building the exercise list from the App component.

```jsx
import './App.css'


function getTitle(title) {
  return title
}
const exercise_list = [
  {
    exercise: 'Bench Press',
    sets: 3,
    reps: 10,
    weight: 135,
    objectID: 0,
  },
  {
    exercise: 'Squats',
    sets: 4,
    reps: 8,
    weight: 185,
    objectID: 1,
  },
  {
    exercise: 'Deadlift',
    sets: 2,
    reps: 5,
    weight: 225,
    objectID: 2,
  },
];

function App() {
  return (
    <div>
      <h1>
        Welcome to {getTitle('The Workout Tracker')}!
      </h1>
      <hr /> 
      <List />
      
    </div>
  )
}

function List() {
  return(
      <ul>
        {exercise_list.map(function(exercise) {
          return (
            <li key={exercise.objectID}>
              {exercise.exercise}: {exercise.sets} sets of {exercise.reps} reps at {exercise.weight} lbs
            </li>
          )
        })}
      
      </ul>)
}

export default App;

```

We can now reference the `List` component within App as an HTML tag to display the component within `App` without changing its functionality.

![[Pasted image 20230730190435.png]]

Each new component represents a single unit of your application which makes the application maintainable and predictable. Once we have defined a component, we can use it as an element anywhere in our JSX. The element represents an **instance** of a component, similar to how a JavaScript class is instantiated.

## Responding to Events

React lets you add _event handlers_ to your JSX. Event handlers are your own functions that will be triggered in response to interactions like clicking, hovering, focusing form inputs, and so on.

**Handler functions** are used to handle events such as clicks, input changes, form submissions, etc. They allow you to define how your application should respond to various user interactions.

You can define a handler function within a React component to handle a specific event. For instance, you might define a function called `handleClick` to respond to a click event. The function is passed as a prop to the HTML element.

Functions passed to event handlers must be passed, not called. For example:
	- `<button onClick={handleClick}>` (correct)
	- `<button onClick={handleClick()}>` (incorrect)

## Props

