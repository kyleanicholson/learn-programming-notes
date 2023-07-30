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

Changing this variable in the source code and seeing the change reflected in the browser is related to React and the development server - whjen the file changes the development server notices and reloads all affected files for the browser. This bridge between React and the development server is called **React Fast Refresh**

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