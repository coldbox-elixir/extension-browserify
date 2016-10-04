# ColdBox Elixir Browserify Support

## Step 1: Install

First ensure, that you're ColdBox Elixir version is up to date. It should be at least version 2 or newer.

```
npm install coldBox-elixir-browserify --save-dev
```

## Step 2: Use It

```js
// Gulpfile.js

var elixir = require( "coldBox-elixir" );

elixir( function( mix ) {
    mix.browserify( "main.js" );
    // mix.browserify(srcPath, outputPath, srcBaseDir, browserifyOptions)
} );
```

This will compile, by default, `resources/assets/js/main.js` to `includes/js/main.js`. Should you require a different source directory, either provide an optional path as the third argument to `mix.browserify`, or begin your path with `./`. This will instruct Elixir to ignore any default base directories.

```js
elixir( function( mix ) {
    mix.browserify( "./app/assets/js/main.js" );
} );
```

The same is true for the output path.

```js
elixir( function( mix ) {
    mix.browserify( "./app/assets/js/main.js", "public/build/bundle.js" );
} );
```

### Custom Options

The fourth argument to the `browserify` method is an `options` object that will be passed through to the browserify task.

```js

elixir( function( mix ){

 mix.browserify( 'main.js', 'includes/javascripts/main.js', 'public/js', {} );

} );

```

### Custom Transformers

While Browserify ships with the [Partialify](https://www.npmjs.com/package/partialify) and [Babelify](https://github.com/babel/babelify) transformers, you're free to install and add more if you wish by doing 2 simple steps:

1. Install the transformer

```

npm install aliasify --save-dev

```

2. update your `Gulpfile.js` by pushing the new transformer configuration via the `elixir.config.js.browserify.transformers` array:

```js

elixir.config.js.browserify.transformers.push( {

 name : 'aliasify',

 options : {}

} );

elixir( function( mix ){

 mix.browserify( 'main.js' );

} );

```
