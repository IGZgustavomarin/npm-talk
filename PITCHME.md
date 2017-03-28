---

## Mastering NPM
![NPM](assets/npm-logo.png)

--- 

# Agenda

- Basic usage
- Create, publish & mantaining modules
- Private & scoped modules

--- 

## Basic usage

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

### Running npm scripts 

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

## Create and publish modules

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

 - Check that you have all basic properties:
   - name, description, author
   - repository
   - license (for public packages) [OSS Licenses](https://opensource.org/licenses/)
 - Always add at least `start` and `test` script.
 - Add a README.md with basic usage information.
 - Read all that can do with your [package.json](https://docs.npmjs.com/files/package.json)

+++ 

### Dependency management

 - You can install normal dependencies and/or development dependencies.
 - Check carefully which one belongs to `dependency` or `devDependency`
 - devDependencies won't be installed when a thirdparty install your module.
 - devDependencies won't be installed if you use `--production` during install.

+++

### Link your package to test

 - During development you can "live" test your package with `npm link`
 
 ```
 $> cd my-package-folder
 $> npm link
 # this will enable your package to install it globally on your system
 $> cd another-folder-to-test-your-module
 $> npm link my-awesome-package
 # your package is installed and you can edit it and see changes here
 ```

+++

### Versioning

 - Use `npm version` to update your `package.json` version. 
 - Use SemVer schema to 
   - Breaking change -> `npm version major`
   - New Feature -> `npm version minor`
   - Bug Fixes -> `npm version patch`
 - Create a CHANGELOG.md to update all  

+++ 

### HINTS 4

- Always check for outdated dependencies
```
$> npm outdated --depth=0 -l 
```
- Prune your dependencies before testing/publishing
```
$> npm prune (--production)
# removes all deps installed not specified on package.json 
```
- Automate your dependencies on CD/CI with tools like [greenkeeper.io](https://greenkeeper.io/) or [renovate](https://github.com/singapore/renovate)
- Use exact version as dependencies (not ^ or ~)

--- 

## Private & Scoped modules

 - NPM Orgs provide private packages, but is a paid solution.
 - If you already have a Nexus manager, use that
 - Use OSS alternatvie like [verdaccio](https://github.com/verdaccio/verdaccio)

+++ 

### Private NPM registry

 - Create a [verdaccio](https://github.com/verdaccio/verdaccio) instance to handle a specific scope, ex: @igz
 - Update your `.npmrc` with your scope
 ```
 //npm.igz.es/:_authToken="YOUR_NPM_ACCESS_TOKEN"
 @igz:registry=https://npm.igz.es/
 ```
 - Now you can publish/install `@igz/my-awesome-package` as a private module.
 
--- 

# FIN.
