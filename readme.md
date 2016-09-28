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

That's it! [Refer to the ColdBox Elixir documentation for more details](https://coldbox-elixir.ortusbooks.com/).
