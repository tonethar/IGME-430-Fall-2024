# 8 - Passing params to `express`

- Here we will start to implement more of the server functionality that `json-server` gave us "for free"
  - specifically, searching for quotes of a specific `id` value

## I. Get Started
- Duplicate the entire **first-routing-app** folder and re-name the copy to **router-app-passing-params**
  - you might want to delete the **node_modules** folder before you make the copy; if so, don't forget to `npm i` below
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
  - here's --> an [article discussing the various ESLint config files](https://medium.com/@ritz.sh/understanding-eslint-configuration-eslintrc-js-vs-eslintrc-vs-eslintrc-json-287ec5e95bf4)
  - https://eslint.org/docs/latest/use/getting-started
- Now add the following `"pretest"` and `"test"` scripts to **package.json**
  - be sure to delete the default `"test"` script

```json
"test": "echo \"Tests Complete!\"",
"pretest": "eslint ./src --fix",
```

### II-A. Run ESLint and Fix the Errors
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
- Add the following to **src/routes/quotes.js** - put this at then end of the file, right before `module.exports = router;`

```js
router.get('/:id', (req, res) => {
  const { id } = req.params;
  console.log(`id=${id}`);
  res.send(data);
});

module.exports = ...
```
- Test the code with - http://localhost:3000/quotes/12345
  - in the Node.js console you should see `id=12345`
- Note that we are using `req.params` this time
  - https://expressjs.com/en/api.html#req.params
- ***YOU DO THIS*** - As we did above, write code that returns the single quote that has a matching `id`
- Test your code:
  - http://localhost:3000/quotes/4c6217c3-c6e5-460b-8f8f-0df64ad6fef2 - returns the Mark Twain quote
  - http://localhost:3000/quotes/6e35a396-c108-4f72-8673-521aa9a3c7f6 - returns the Elbert Hubbard quote
  - http://localhost:3000/quotes/12345 - returns `{}`
  - http://localhost:3000/quotes/ - still returns all the quotes

---

## VI. Refactor time
- Your version of the code likely has one or more quality issues that need to be addressed:
  - ESLint airbnb/base does not like using a `for` loop on arrays, and prefers a more functional style with methods like `.map()`, `.forEach()`, `.find()` etc
  - you might have some duplicated code that needs to be factored out
  - we have "model" code (the quotes data) mixed in with our routing code (a "controller") - these should be separated

---

### VI-A. quotes-data.json
- In the **src/** folder, create a **data** folder
- Here is **quotes-data.json** - now we are up to 5 quotes - put this is the **src/data/** folder

**src/data/quotes-data.json** 

```js
{
  "version": "2.0",
  "quotes": [
    {
      "id": "4c951b60-1f90-41e7-a913-c1f454ff4c6e",
      "author": "Oscar Wilde",
      "content": "Be yourself; everyone else is already taken.",
      "tags": [
        "uncategorized"
      ],
      "createdAt": "2024-08-01T04:00:00.000Z",
      "updatedAt": "2024-08-01T04:00:00.000Z"
    },
    {
      "id": "4c6217c3-c6e5-460b-8f8f-0df64ad6fef2",
      "author": "Mark Twain",
      "content": "If you tell the truth, you don't have to remember anything.",
      "tags": [
        "uncategorized"
      ],
      "createdAt": "2024-08-01T04:00:00.000Z",
      "updatedAt": "2024-08-01T04:00:00.000Z"
    },
    {
      "id": "6e35a396-c108-4f72-8673-521aa9a3c7f6",
      "author": "Elbert Hubbard",
      "content": "A friend is someone who knows all about you and still loves you.",
      "tags": [
        "uncategorized"
      ],
      "createdAt": "2024-08-01T04:00:00.000Z",
      "updatedAt": "2024-08-01T04:00:00.000Z"
    },
    {
      "id": "4f19e53d-8b5b-40ab-ba72-cfbbcd2ce4f6",
      "author": "J.K. Rowling",
      "content": "It does not do to dwell on dreams and forget to live.",
      "tags": [
        "fiction"
      ],
      "createdAt": "2024-08-01T04:00:00.000Z",
      "updatedAt": "2024-08-01T04:00:00.000Z"
    },
    {
      "id": "7690718f-01b7-4775-9998-6a4adb480d27",
      "author": "Thomas Sowell",
      "content": "When you want to help people, you tell them the truth. When you want to help yourself, you tell them what they want to hear.",
      "tags": [
        "uncategorized"
      ],
      "createdAt": "2024-08-01T04:00:00.000Z",
      "updatedAt": "2024-08-01T04:00:00.000Z"
    }
  ]
}
```

---

### VI-B. db.js
- "db" is short for "database"
- we will have it load in our **quotes-data.js** file
- put this in the **src/** folder
- it will (eventually) have methods that **C**reate, **R**ead, **U**pdate & **D**elete (**CRUD**) the quotes data

**src/db.js**

```js
const fs = require('fs');
const path = require('path');

const quotesPath = path.resolve(__dirname, 'data/quotes-data.json');
const jsonString = fs.readFileSync(quotesPath);
const data = JSON.parse(jsonString);
const { quotes } = data; // object destructuring

// PUBLIC METHODS
const getAllQuotes = () => quotes;

module.exports = { getAllQuotes };

```

---

### VI-C. Utilize db.js

- Now head back to **src/router/quotes.js**
  - import **db.js** with (put this near top of file):
    - `const db = require('../db.js');`
- At the top of **src/router/quotes.js** where we are declaring `const data=[{...]`, which is the hard-coded array of 3 quotes:
  - replace that code with `const data = db.getAllQuotes();` - which will use the array of 5 quotes that **db.js** is loading in from **quotes-data.json**
- Test your code:
  - http://localhost:3000/quotes/4f19e53d-8b5b-40ab-ba72-cfbbcd2ce4f6 - returns the JK Rowling quote
  - http://localhost:3000/quotes/?id=6e35a396-c108-4f72-8673-521aa9a3c7f6 - returns the Elbert Hubbard quote
  - http://localhost:3000/quotes/random - returns a random quote
  - http://localhost:3000/quotes/recent  - returns the Thomas Sowell quote
  - http://localhost:3000/quotes/12345 - returns `{}`
  - http://localhost:3000/quotes/ - still returns all the quotes
  - http://localhost:3000/rich-client.html - the buttons still work!

---

## VII. Homework
- In **src/db.js**:
  - create a `randomQuote()` function that returns a random quote from `data.quotes`, and export it
  - create a `recentQuote()` function that returns the last element of `data.quotes`, and export it
  - create a `getQuoteById(id)` function that returns the quote in `data.quotes` with the matching `id`, and export it
    - utilize `array.find()`
    - if there is not a quote with a matching `id`, the function will return `undefined`
- In **src/routes/quotes.js**
  - utilize all 3 functions above `db.randomQuote()`, `db.recentQuote()`, and `db.getQuoteById()`
  - AND delete unnecessary code - for example:

```js
// DELETE THIS!
router.get('/random', (req, res) => {
  const quote = data[Math.floor(Math.random() * data.length)];
  res.json(quote);
});

// REPLACE IT WITH THIS!
router.get('/random', (req, res) => {
  res.json(db.randomQuote());
});
```
- Test all of the above links again to be sure that everything still works
- Run `npm test` and fix all errors

---

## VIII. Homework Submission
- ZIP and POST the entire folder to the myCourses dropbox:
  - don't neglect to delete the **node_modules** folder BEFORE zipping
  - there is no need to post this to GitHub or Heroku
 

---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**7 - Express Routing**](7-express-routing.md)  |  [**IGME-430**](../) | [**9 - Putting our project on Heroku**](9-putting-project-on-heroku.md)

