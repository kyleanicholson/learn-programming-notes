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