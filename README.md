# A React Journey
## A tour of the latest trends in the React ecosystem

### TOC

* Webpack
* CSS Modules
* Babel / ES6
* React
* Redux
* Mobx
* Enzyme


### Webpack
v1.1.x -> https://webpack.github.io/
v2 -> https://webpack.github.io/docs/roadmap.html

good tutorial -> http://www.pro-react.com/materials/appendixA/


#### Loaders

* test:  A regular expression that matches the file extensions that should run through this loader (Required).
* loader:  The name of the loader (Required).
* include / exclude:   Optional setting to manually set which folders and files the loader should explicitly add or ignore.
* query:  The query setting can be used to pass Additional options to the loader.

```
loaders: [
  { test: /\.css$/, loader: "style!css" },
  {
    test: /\.js$/,
    exclude: /node_modules/,
    loader: 'babel',
    query: {
      presets: ['es2015','react']
    }
  }
]
```

The exclamation point ("!") can be used in a loader configuration to chain different loaders to the same file types.

##### CSS Modules
https://css-modules.github.io/webpack-demo/
```
{
  test: /\.css$/,
  loader: 'style!css?modules'

  or
  
  loaders: [
    'style-loader',
    'css-loader?modules&sourceMap&importLoaders=1&localIdentName=[name]__[local]___[hash:base64:5]',
  ]
}
```
