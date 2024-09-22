# 8 - Passing params to `express`

- Here we will start to implement more of the server functionality that `json-server` gave us "for free"
  - specifically, searching for quotes of a specific `id` value

## I. Get Started
- Duplicate the entire **first-routing-app** folder and re-name the copy to **router-app-passing-params**
  - you might want to delete the **node_modules** folder before you make the copy; if so, don't forget to `npm i`
- Open up **router-app-passing-params** in VSCode and `npm i`,  `npm run dev`
- Verify that the app's endpoints still work in the browser

---

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
- Now add the following "pretest" and "test" scripts to **package.json**
  - be sure to delete the default `"test"` script

```json
"test": "echo \"Tests Complete!\"",
"pretest": "eslint ./src --fix",
```

## II-A. Run ESLint and Fix the Errors
- Type `npm test` to see all of the errors and warnings
- Miraculously, I only got 1 warning - a `console.log()` - and 1 error - in our "fallthrough" route located in **index.js**:

```
router-app-passing-params/src/app.js 29:20  error 'next' is defined but never used  no-unused-vars
```

- Which was easy to fix - go ahead and delete the `next` param - we don't need it
- Go ahead and fix any other errors and move on

---

## III. Discussion

- Currently, the `/quotes` endpoint returns an *entire array* of quotes...
- ... but what if the user of this API was only interested in a *single* quote of a particular `.id`?
- If we passed the *entire array* of quotes back to the user it would not be a big deal yet because we only have 3 total quotes ...
- ... but what if we had 3000 (or 30,000) quotes in our database? Sending *all* of the quotes won't scale and our server would either run out of bandwidth or start costing iu a lot!
- Solution: Send back just the one quote the user is interested in.
- Commonly, because of API *conventions* (common practice), they might ask for the endpoint for a single quote using one of these techniques:
  - a `GET` request: `/quotes/?id=12345` - using the *query string* to pass in an `id` parameter value of `12345`
  - a `GET` request: `/quotes/12345` - using a URL *route* to pass in a value, which our code will assume is an `id` value

---

## IV. Accessing query parameters with `express`
- First, let's consider how to do the *query string* version - here we'll use `request.query`, which gives us an object containing all of the query parameters and their values:
  - https://expressjs.com/en/api.html#req.query
  - https://www.geeksforgeeks.org/express-js-req-query-property/
- Let's set up our `routes/quotes` route to grab `routes/quotes?id=12345`
- Add the following to **src/routes/quotes.js**, at the top of the existing `router.get('/', ...` route handler

---

```js
router.get('/', (req, res) => {
  const { id } = req.query; // note: ESLint airbnb/base insists on object destructuring syntax!
  console.log(`id=${id}`);
  ...
}
```

---

- `npm run dev` to start the server
- In the browser (or Postman) head to http://localhost:3000/quotes/?id=4
  - check the node.js terminal, you should see `id=4` logged out
- In the browser (or Postman) head to http://localhost:3000/quotes/?index=4
  - check the node.js terminal, you should see `id=undefined` logged out
  - Why? Because we never passed in a value for `id`, and our code is ignoring `?index=4`
- If you want to see ALL the query params logged out:
  - add `console.log('req.query=', req.query);`
  - head to http://localhost:3000/quotes/?id=4&param2=value2&param3=value3&param4=value4
  - check the node terminal to see `req.query= { id: '4', param2: 'value2', param3: 'value3', param4: 'value4' }`
 
---

***YOU DO THIS*** - write code that returns the single quote that has a matching `id`:
- `quotes.find()` would be the most elegant solution, but using a `for` loop is fine for now
- if there is not a matching quote, return an empty `{}`
- if the `id` parameter does not exist or has no value, return *ALL* of the quotes as we did before
- Test your code:
  - http://localhost:3000/quotes/?id=4c6217c3-c6e5-460b-8f8f-0df64ad6fef2 - returns the Mark Twain quote
  - http://localhost:3000/quotes/?id=6e35a396-c108-4f72-8673-521aa9a3c7f6 - returns the Elbert Hubbard quote
  - http://localhost:3000/quotes/?id=12345 - returns `{}`
  - http://localhost:3000/quotes/ - still returns all the quotes

---

## V. Accessing parameters via the route
- Another way to pass in parameters to a web script is via the route, like this
- `http://localhost:3000/quotes/12345` - "give me the quote with an id of `12345`"
  - if we try this URL right now we'lll just get a 404 page
- Let's get coding and get this endpoint working!
- Add the following to **src/routes/quotes.js**:

```js

```

