---

## Mastering NPM
![NPM](assets/npm-logo.png)

--- 

## But first, the basis

+++

### Everyday commands

```sh
$> npm install <module_name> --save  (-S)
# install a new packages and adds it to `package.json
```
```sh
$> npm install <module_name> --save-dev (-D) 
# install a new development packages and adds it to `package.json
``` 

+++ 

#### HINTS 1

- Use `--save-exact` (or `-E`) to save exact versions of a package
- Or setup `npm` to do it by default: 

```
$> npm config set save-exact=true
$> cat ~/.npmrc
```

+++

### Running npm  scripts 

You can create all your scripts inside `package.json` to run with a npm command: 

```sh
$> npm run <script-name>
# run a script from package.json named "script-name" 
``` 

+++

### Special scripts

 - ```start``` and `test` are special scripts that doesn't need the `run` parameter. 
 - These scripts are commonly used to run your project or run your test suites respectively.

```
$> npm start  # same as npm run start
$> npm test
``` 

+++ 

### Scripts lifecycle

- All npm scripts have a "pre" and "post" stage. So if you create `task1`, npm will check `package.json` for a  `pretask1` and `posttask1` scripts and run them if anyone is present.

+++ 

### HINTS 2

Remember that `./node_modules/.bin` is already in the running script $PATH. Don't write it in your `package.json`. Example: 

```js
{
   "scripts": {
      "bad-script": "./node_modules/.bin/cucumberjs test/acceptance -r test/step_definitions",
      "good-script": "cucumberjs test/acceptance -r test/step_definitions"
   }
}

``` 

+++ 

### HINTS 3

 - Avoid using global packages, install all as a local dependency and run commands through an npm script. 
 - You can also add `./node_modules/.bin/` to your $PATH and run commands as if they were global, but it'll always check for a local version first. 

---

## Creating a new module

+++

### Init your package

- Create an empty folder
- Don't create a `package.json` manually
- Use npm to setup your `package.json`

```sh
$> npm init -y 
name: (my-super-package)
version: (1.0.0)
description: This package is awesome
git repository:
author:
license: (ISC)
About to write to package.json:
{
    "name": "my-super-package",
    "version": "1.0.0",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [],
    "author": "",
    "license": "ISC",
    "description": "This package is awesome"
}
``` 

+++ 

### Enhance your `package.json` 

- Read all that can do with your [package.json](https://docs.npmjs.com/files/package.json)

--- 

# FIN.
