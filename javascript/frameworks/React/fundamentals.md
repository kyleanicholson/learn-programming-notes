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

As a React app grows, there are an increasing number of components to manage. Each component encapsulates or abstracts a meaningful task or idea while contributing to the overall project goals.

In our example app, for example, we may want to abstract the process of building the exercise list from the App component.

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

**Props** allow us to pass variables as information from one component to another component. These variables can only be passed to descendant components and cannot be used to move information from descendent components to parent components.

*src/App.jsx*
```jsx
const App = () => {
  const workouts = [
  {
    title: "Bench Day",
    muscle_groups: "Chest and Shoulders",
    day_of_week: "Monday",
    date: "2023-07-15",
    exercises: [
      "Bench Press",
      "Tricep Extension",
      "Chin Ups",
      "Side Lateral Raise",
    ],
    objectID: 0,
  },
  {
    title: "Leg Day",
    muscle_groups: "Legs",
    day_of_week: "Wednesday",
    date: "2023-07-19",
    exercises: ["Squats", "Leg Press", "Lunges", "Calf Raises"],
    objectID: 1,
  },
  {
    title: "Back Day",
    muscle_groups: "Back, Biceps",
    day_of_week: "Friday",
    date: "2023-07-21",
    exercises: ["Deadlift", "Pull Ups", "Bent Over Row", "Bicep Curls"],
    objectID: 2,
  },

];
return (
  <div>
    <h1>Welcome to {getTitle(title)}!</h1>
    <Search />
    <hr />
    <div id="workout-list">
    <WorkoutList list={workouts}/>
    </div>
  </div>
);
};

const WorkoutList = (props) => (
  <ul>
    {props.list.map((item) => (
      <Workout key={item.objectID} item={item} />  
    
    ))}
  </ul>
);


const Workout = (props) => (
  <li className="workout-item">
    <h4 className="workout-title">{props.item.title}</h4>
    <div className="workout-details">
      <p className="workout-muscle-groups">Muscle Groups: {props.item.muscle_groups}</p>
      <p className="workout-date">Date: {props.item.day_of_week}, {props.item.date}</p>
    </div>
    <ul className="workout-exercises">
      {props.item.exercises.map((exercise, index) => (
        <li key={index} className="workout-exercise">
          {exercise}
        </li>
      ))}
    </ul>
  </li>
);
	  
```

### PropTypes

When I first tried to run the above code it did not run and I received errors about props validation. I used ChatGPT to research this error and learned that I would need to install and import a separate library known as prop-types to fix these issues.

PropTypes is a mechanism for validating the props that are passed to a component. It allows you to specify the expected types and structure of the props, ensuring that they meet certain requirements before being used by the component. This helps catch potential bugs and provides better documentation for your components.

 If you haven't already installed prop-types, you can do so by running the following command:
```bash
npm install prop-types
```

Once installed, you can import and use it in your components.

```bash
import PropTypes from 'prop-types';
```


These prop-types were generated by ChatGPT for my workout data. I tested and they worked once I restarted my app and the errors no longer displayed.

*src/App.jsx*
```jsx
Workout.propTypes = {
  item: PropTypes.shape({
    title: PropTypes.string.isRequired,
    muscle_groups: PropTypes.string.isRequired,
    day_of_week: PropTypes.string.isRequired,
    date: PropTypes.string.isRequired,
    exercises: PropTypes.arrayOf(PropTypes.string).isRequired,
    objectID: PropTypes.number.isRequired,
  }).isRequired,
};

WorkoutList.propTypes = {
  list: PropTypes.arrayOf(
    PropTypes.shape({
      title: PropTypes.string.isRequired,
      muscle_groups: PropTypes.string.isRequired,
      day_of_week: PropTypes.string.isRequired,
      date: PropTypes.string.isRequired,
      exercises: PropTypes.arrayOf(PropTypes.string).isRequired,
      objectID: PropTypes.number.isRequired,
    })
  ).isRequired,
};
```

Before moving on, I wanted to make sure I understood what these were actually doing--I never let ChatGPT code slide without making sure I know how it works.

Each use of .propTypes defines the general 'shape' of a prop. A prop can be an object, an array of objects, or (I suspect) a variety of different forms of embedded data structures (objects within objects, lists, within objects, etc.)  Essentially the.PropTypes method on the component outlines the overall format the data contained within a prop must have in order be passed successfully down the component hierarchy.

Furthermore, the PropTypes in these cases contain key-value pairs, in which the keys correspond to the original object's keys and the values use different methods from the PropTypes object to define what 'type' the variable should have. In other words, 'title' should contain a string, whereas objectID should contain a number. Exercises should an 'arrayOf' strings.

Finally, all of these properties are marked as required, meaning the prop must be present when using the component.

In summary, properties or 'props' allow us to pass information down the component hierarchy from parent components to child components. They are vehicles to transport information which can 'talk' to their descendant components.  PropTypes  perform typechecking to make sure the data received is valid.

*note: According to React's website, PropTypes aren’t commonly used in modern React. Use TypeScript for static type checking.*

### useState function

useState method tells react that we want to have a 'stateful' value which changes over time. Whenever this stateful value changes, the affected components will re-render to use it. The useState function is called a **React hook** - it's one of many hooks provided by react.

useState takes an *initial state* as an argument - for example an empty string for a blank search field. 

```jsx
const Search = () => {
  // perform a task in response to an event
  const [searchTerm, setSearchTerm] = useState("");
  const handleChange = (event) => {
  setSearchTerm(event.target.value);
  };
  return (
    <div>
      <label htmlFor="search">Find Workout: </label>
      <input id="search" type="text" onChange={handleChange} />
      <p>
        Searching for <strong>{searchTerm}</strong>.
      </p>
    </div>
  );
};
```

React re-renders this component (and all of its potential descendant components) after its state has changed. In essence, every component in a React application has one initial rendering followed by potential re-renderings. Whenever a user interaction occurs, the change is captured in React's state which forces a re-rendering of all components affected by this change.

### Callback Handlers

Callback handlers are functions that allow us to pass information up the component tree. A callback handler gets introduced as an event handler, is passed as a function in props to another component, is executed there as a callback handler, and calls back to the place it was introduced.

