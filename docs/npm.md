# NPM Scripts

## Table of Contents

- SCSS Compiler

## SCSS Compiler

> Folder structure options and naming conventions for software projects

### Install SASS compiler

```
$ npm install node-sass --save-dev
```

### create a folder structure and required files

```
$ mkdir sass
$ mkdir dist
$ cd sass
$ cd touch main.scss
$ cd ../dist
$ touch style.scss
```

    .
    ├── build                   # Compiled files (alternatively `dist`)
    ├── sass                    # Test files (alternatively `spec` or `tests`)
    │   └── main.scss           # Load and stress tests
    ├── dist                    # Test files (alternatively `spec` or `tests`)
    │   └── style.scss          # Load and stress tests
    └── package.json            # Documentation files (alternatively `doc`)

package.json

```
"scripts": {
    "compile:sass": "node-sass sass/main.scss css/style.css -w"
  },
```

### run compiler

```
npm run compile:sass
```

## Optional : Automatic Reload Page Changes

### Install NPM Live Server

source : https://www.npmjs.com/package/live-server

```
$ npm install -g live-server
```
