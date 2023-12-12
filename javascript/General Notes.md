- You can use the `fetch` function to get data from an endpoint (url) -- for example JSON data for cities
```js
const endpoint =

"https://gist.githubusercontent.com/Miserlou/c5cd8364bf9b2420bb29/raw/2bf258763cdddd704f8ffd3ea9a3e81d25e2c6f6/cities.json";


const cities = [];


fetch(endpoint)

.then((blob) => blob.json())

.then((data) => cities.push(...data));

console.log(cities)
```
* You can use regular expressions to filter a list down based on a user's input.

```js
function findMatches(wordToMatch, cities) {

return cities.filter((place) => {

// Figure out if the city or state matches what was searched

const regex = new RegExp(wordToMatch, "gi"); // gi = Global and case insensitive

return place.city.match(regex) || place.state.match(regex); // match function searches string for the regular expression - returns an array object if the match is found

});

}
```

- When you use querySelector to select an element (for example an input), you can use this.value to check the current value of the element. You can then add an event listener to the element to detect when the element changes or a keyboard event takes place to call the function when that event occurs.
- 
```js
  
  const searchInput = document.querySelector(".search");
  searchInput.addEventListener("change", displayMatches);
  searchInput.addEventListener("keyup", displayMatches);
  
```

- `${}` inside of backticks allows you to inject javascript within html. These are called 'template literals'
```js
function generateHTML(personName, age) {
  const html = `
    <div>
      <h2>Name: ${personName}</h2>
      <p>Age: ${age}</p>
    </div>
  `;
  return html;
}

const name = "John";
const age = 30;
const resultHTML = generateHTML(name, age);
console.log(resultHTML);

```