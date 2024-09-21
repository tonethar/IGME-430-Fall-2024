# 8 - Passing Params in express

## I. Get Started
- Duplicate the entire **first-routing-app** folder and re-name the copy to **router-app-passing-params**
  - you might want to delete the **node_modules** folder before you make the copy; if so, don't forget to `npm i`
- Open up **router-app-passing-params** in VSCode and `npm i`,  `npm run dev`
- Verify that the app's endpoints still work in the browser

## II. ESLint
- We are eventually going to be pushing this app to Heroku, so let's go ahead and get ESLint set up for this project
- In VSCode's terminal (Windows folks be sure you are using GitBash), type `pwd` and verify that your *current working directory* is `router-app-passing-params/`
- Install ESLint as a developer dependency - type:
  - `npm i -D eslint eslint-config-airbnb eslint-plugin-import`
- Create an empty **.eslintrc** config file - type:
  - `touch .eslintrc`
- Make the contents of **.eslintrc** look like this:

```json
{ 
  "extends": "airbnb/base",
  "rules": {
    "no-underscore-dangle" : "off",
	  "no-plusplus": "off",
    "import/extensions": "off"
  }
}
```

- By the way:
  - here's an [article discussing the various ESLint config files](https://medium.com/@ritz.sh/understanding-eslint-configuration-eslintrc-js-vs-eslintrc-vs-eslintrc-json-287ec5e95bf4)
  - https://eslint.org/docs/latest/use/getting-started
- Now add the following "pretest" and "test" scripts to **package.json**:

```json
"test": "echo \"Tests Complete!\"",
"pretest": "eslint ./src --fix",
```
