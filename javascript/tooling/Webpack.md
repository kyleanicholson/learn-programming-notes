
https://webpack.js.org/guides/getting-started/

**Webpack and Module Bundlers**: As projects grow in complexity, organizing code into modules becomes beneficial. Webpack is introduced as a tool to bundle multiple files and third-party libraries into fewer files to reduce HTTP requests, improving load times and performance. 

If you give webpack a file as an entry point usually a `src` folder, it will build a dependency graph based on all the imports/exports starting there, before bundling everything into a single `.js` file in `dist`.

[HTML-webpack-plugin](https://www.theodinproject.com/lessons/node-path-javascript-webpack#html-webpack-plugin) can be used to automatically build an HTML file in dist
```js
// webpack.config.js

const HtmlWebpackPlugin = require('html-webpack-plugin');

// ...
    plugins: [
        new HtmlWebpackPlugin({
            template: './src/template.html',
        }),
    ],
// ...

```