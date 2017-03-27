---

## Mastering NPM
![NPM](assets/npm-logo.png)

--- 

## But first, the basis

+++

### Everyday commands

```
$> npm install <module_name> --save  (-S)
# install a new packages and adds it to `package.json

$> npm install <module_name> --save-dev (-D) 
# install a new development packages and adds it to `package.json
``` 

+++ 

#### HINTS 1

- Use `-E` to save exact versions of packages
- Or setup `npm` to do it by default: 

```
$> npm config set save-exact=true
$> cat ~/.npmrc
```

### Running default scripts 

- `npm start`
  - default npm-script in `package.json` to start your project.
- `npm test`
  - default npm-script in `package.json` to test your project.

+++

### Running other scripts

- `npm run`
  - shows all your npm-scripts in `package.json`
- `npm run <script-name>`
  - run a different script than `start` or `test`
  

--- 

# FIN.
