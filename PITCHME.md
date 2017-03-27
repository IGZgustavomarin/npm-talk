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

--- 

# FIN.
