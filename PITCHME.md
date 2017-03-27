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

If you install dependencies to run from your scripts (webpack, cucumber, mocha, etc), you don't need to specify the complete path in the script, as `node_modules/.bin` is already on the $PATH of the running script.

Example: 

```js
{
   "scripts": {
      "bad-script": "./node_modules/.bin/cucumberjs test/acceptance -r test/step_definitions",
      "good-script": "cucumberjs test/acceptance -r test/step_definitions"
   }
}

``` 

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

--- 

# FIN.
