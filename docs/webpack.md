# Webpack

Install webpack

```
$ npm install webpack --save-dev
```

Create Directory

```
  Site Name
  |- package.json
+ |- /dist
+   |- index.html
+ |- /src
+   |- app.js
```

## Installing Bootstrap

> Use the following command to install Bootstrap and its peer dependencies, jQuery and Popper:

`$ npm install bootstrap jquery popper.js --save`

> If you choose to import Bootstrap’s JavaScript plugins individually as needed, you must also install exports-loader.

`$ npm install exports-loader --save-dev`

> You’ll need to install the required loaders and postcss plugins for compiling and bundling Bootstrap precompiled Sass files.

`$ npm install autoprefixer css-loader node-sass postcss-loader sass-loader style-loader --save-dev`

## Webpack configuration file

> Create a webpack configuration file. The example configuration file included below assumes you’ll be using the Boostrap Sass source files as part of your project’s bundling process.

webpack.config.js

```javascript
const path = require('path');

module.exports = {
  entry: './src/app.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  },
  module: {
    rules: [
      {
        test: /\.(scss)$/,
        use: [
          {
            // Adds CSS to the DOM by injecting a `<style>` tag
            loader: 'style-loader'
          },
          {
            // Interprets `@import` and `url()` like `import/require()` and will resolve them
            loader: 'css-loader'
          },
          {
            // Loader for webpack to process CSS with PostCSS
            loader: 'postcss-loader',
            options: {
              plugins: function() {
                return [require('autoprefixer')];
              }
            }
          },
          {
            // Loads a SASS/SCSS file and compiles it to CSS
            loader: 'sass-loader'
          }
        ]
      }
    ]
  }
};
```

## Importing Bootstrap JavaScript

> Import Bootstrap’s JavaScript by adding this line to your app’s entry point /src/app.js:

```
import 'bootstrap';
```

## Importing Bootstrap Sass

> When importing Bootstrap’s Sass source files you can include all of Bootstrap, or pick only the parts you need. Update your project’s directory structure and create a new file /src/scss/app.scss.

```
|- /src
    |- app.js
+   |- /scss
+   |- app.scss
```

> Import all of Bootstrap’s Sass by adding this line to app.scss

```
@import "~bootstrap/scss/bootstrap";
```

> Finally, include Bootstrap’s Sass in your bundle by adding this line to your app’s entry point /src/app.js:

```
import './scss/app.scss';
```

## Bundling with Webpack

> Edit your package.json file to add a npm script to run the webpack command.

```javascript
"scripts": {
    "build": "webpack --watch"
  },
```

> You may now use the npm run build command to build your bundle with Webpack.

```bash
$ npm run build
```
