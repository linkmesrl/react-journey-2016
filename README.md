# A React Journey
## A tour of the latest trends in the React ecosystem

### TOC

* Webpack
* CSS Modules
* Babel / ES6
* React
* Redux
* Mobxr
* Enzyme


### Webpack
v1.1.x -> https://webpack.github.io/
v2 -> https://webpack.github.io/docs/roadmap.html

good tutorial -> http://www.pro-react.com/materials/appendixA/
`npm install webpack -g`

`webpack.config.js`

```
module.exports = {
    entry: "./entry.js",
    output: {
        path: __dirname,
        filename: "bundle.js"
    },
    module: {
        loaders: [
            { test: /\.css$/, loader: "style!css" }
        ]
    }
};
```
