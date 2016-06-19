# Webpack

## webpack-validator
Error difficult to follow:  
Could be handy `webpack-validator` package to validate our webpack script

Install the npm and use the cli webpack-validator to check the webpack.config with env variables.


## babel-preset-es2015-webpack
Leave to webpack the modules exports, it can find unused classes and tell problems because they will static analyze es6 modules. It's not commonjs anymore.
Tree shaking. Modify the babel preset too.

## Add promise api polyfill
To make sure every browser will support promises  
http://cdn.polyfill.io

## webpack code splitting
System.import('./URL_TO_MODULE').then()

Import bundle dinamicaly, it will return a promise.

## long term caching
bundle.[chinkhash].js in webpack.config.js
html-webpack-plugin -> template: ./index.html

## Grouping vendor files
common chunk plugin, built in webpack directly. You don't need another npm.
```javascript
entry: {
  app: './js/app.js',
  vendor: ['lodash', 'jquery'],
}
output: {
  filename: 'bundle.[name].js'
  ...
}
```
```javascript
plugins: [
  new webpack.optimize.CommonsChunkPlugin({ name: 'vendor' })
]
```

## commons from multiple appxs
```javascript
plugins: [
  new webpack.optimize.CommonsChunkPlugin({ name: 'common', filename: 'bundle.common.js' }),
  new webpack.optimize.CommonsChunkPlugin({ name: 'vendor', chunks: ['app', 'animalFact'] }),
]
```

## Optimization
remove the -p from npm script and add those plugins for production
- `webpack.optimize.DedupPlugin()`
- `webpack.LoaderOptionsPlugin({
    minimize: true,
    debug: false,
  })` // available in webpack 2
- `webpack.DefinePlugin({
    'process.env': {
      NODE_ENV: '"production"',
    },
  })`
- `webpack.optimize.UglifyJsPlugin({
    compress: {
      screw_ie8: true, // eslint-disable-line
      warnings: false,
    }
  })`

## Expose modules to dependencies
`imports-loader`
```javascript
{
  test: require.resolve('./src/js/non_npm_module'),
  loader: 'imports?_=lodash'
}
```

## import non es6 modules
`exports loader`

```javascript
import leftPad from 'exports?leftPad!./non_node_modules/left-pad'
```
to remove it also from global object:
`imports-loader`

```javascript
import leftPad from 'imports?window=>{}!exports?leftPad!./non_node_modules/left-pad'
```

```javascript
{
  test: require.resolve('./src/js/non_npm_module/...'),
  loaders: ['imports?window=>{}', 'exports?leftPad']
}
```
