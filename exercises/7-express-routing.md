# 7 - `express` Routing

## Overview
- *Routing* refers to determining how an application responds to a client request for a particular endpoint
- *Routing libraries* make it easy to organize your app's *routes* - for example `/home`, `/quotes`, `/quotes/id`, `quotes/random`, `quotes/random/5` etc
- We are going to re-architect **first-express-app** to use a routing library

---

## I. Get Started
- Duplicate the entire **first-express-app** folder and re-name the copy to **first-routing-app**
  - you might want to delete the **node_modules** folder before you make the copy; if so, don't forget to `npm i` below
- Open up **first-routing-app** in VSCode and `npm i`,  `npm run dev`
- Verify that the app's endpoints still work in the browser

---

## II. Cleaning up the code

- In **app.js**, go ahead and comment out (don't delete them yet) all your existing routes - meaning you should only have the first 6 lines of code or so, and the last line of code. Example:

```js
const express = require('express');
const port = 3000;
const path = require('path');
const filePath404Page = path.resolve(__dirname,'../client/404.html');
const app = express();
app.use(express.static('client'));

// ** COMMENT OUT ALL THE ROUTES **

app.listen(port, () => {
  console.log(`App running on http://localhost:${port}`);
});
```

- Test it in the browser:
  - your static files will still be served up
  - `/`, `/bye`, `helloJSON`, etc endpoints will no longer function and will give the `Cannot GET ...` message 

---

## III. Adding the router
- Inside your **src/** directory, create a **routes** directory
- Inside of **src/routes/**, create a **index.js** file
- Make **index.js** look like this:

**index.js**
```js
const express = require('express');
const router = express.Router();

router.get('/', (req, res)=> {
  res.send('Hello world!');
});

module.exports = router;
```

---

- You can see above that we have created a `router` instance, and have attached our `/` route to it
- To utilize this `/` route, and the other routes we will be adding soon, add the following code to **app.js**:

**app.js**
```js
...

// import routes (put this near top)
const indexRouter = require('./routes/index.js');

// use routes (put this near the bottom, BEFORE app.listen()
app.use('/', indexRouter);

...
```

- Now head to http://localhost:3000/ in the browser - you should see the `Hello world!` message!
  - go ahead and delete the commented out `app.get('/', ...` code in **app.js** - you don't need it any more

---

- ***\*\* YOU TRY THIS \*\**** --> Now implement the `/bye` endpoint in **index.js**


<details>
  <summary><b>Solution for <kbd>/bye</kbd> in index.js</b></summary>
  <code>
    
  router.get('/bye', (req, res) => {
    res.send('Goodbye!');
  });
    
  </code>
</details>

- Now head to http://localhost:3000/bye in the browser - you should see the `Goodbye!` message!
  - go ahead and delete the commented out `app.get('/bye', ...` code in **app.js** - you don't need it any more

---

- ***\*\* YOU DO THIS \*\**** --> Now implement the `/helloJSON` endpoint in **index.js**
- ***\*\* YOU DO THIS \*\**** --> Now implement the `/timeJSON` endpoint in **index.js**
- Test the endpoints in the browser:
  - http://localhost:3000/helloJSON
  - http://localhost:3000/timeJSON
- Code you can now delete:
   - the commented out versions of `/helloJSON` and `/timeJSON` endpoint in **app.js**
   - the `app.post('/addComment', ...)` code in **app.js** (we'll handle express POST operations in a future exercise)
- Open --> http://localhost:3000/rich-client.html
  - this endpoint is being served by `express.static()`
  - test both buttons - because we have restored the `/helloJSON`  and `/timeJSON`  endpoints, they should work as before

---

## IV. Bring Back the `404` page!

- If you head to http://localhost:3000/qwerty - you'll see that our custom `404` page is not showing and we're just getting the express default `Cannot GET /qwerty` message
- Let's fix that! Add this to **app.js** - this will be the LAST route before `app.listen()`

```js
...

// this is the LAST route, right before app.listen()
app.use((req, res, next) => {
  res.status(404).sendFile(filePath404Page);
})

// app.listen(...)
```

- Reference: ***How do I handle 404 responses?*** - https://expressjs.com/en/starter/faq.html  

---

## V. More routes - the `quotes/` API!
- So far, we have cleaned up **app.js** quite a bit by moving all the "top level" endpoints over to **src/routes/index.js**
- But we have not yet fully seen how this pattern can help us write easier to maintain code
- So let's go ahead and create a read-only (for now) quotes API

### V-A. New router file - quotes.js

- Inside of **src/routes/** go ahead and create a **quotes.js** file
- Make it look like this:

```js
const express = require('express');
const router = express.Router();

// just 3 quotes for now
const data = [{
  "id": "4c951b60-1f90-41e7-a913-c1f454ff4c6e",
  "author": "Oscar Wilde",
  "content": "Be yourself; everyone else is already taken."
  },
  {
  "id": "4c6217c3-c6e5-460b-8f8f-0df64ad6fef2",
  "author": "Mark Twain",
  "content": "If you tell the truth, you don't have to remember anything."
  },
  {
  "id": "6e35a396-c108-4f72-8673-521aa9a3c7f6",
  "author": "Elbert Hubbard",
  "content": "A friend is someone who knows all about you and still loves you.",
  }
];

router.get('/', (req, res)=> {
  res.json(data);
});


module.exports = router;

```

---

### V-B. Import these routes into app.js

```js
// import routes (put this near top)
// ...
const quotesRouter = require('./routes/quotes.js');

// use routes (put this near the bottom, BEFORE app.listen()
// ...
app.use('/quotes', quotesRouter); // now /quotes is a route!

```

- Test it here - http://localhost:3000/quotes/ - and you should see the entire `data` array returned as JSON

---

### V-C. Create a `/quotes/random` endpoint!

- ***\*\* YOU DO THIS \*\**** --> Now implement the `/quotes/random` endpoint in **routes/quotes.js**
- Hint: you only need to add code to **routes/quotes.js**, **app.js** is all set and doe not need any more code!
- Test it at --> http://localhost:3000/quotes/random

<details>
  <summary><b>Solution for <kbd>/quotes/random</kbd> in routes/quotes.js</b></summary>
  <code>
   router.get('/random', (req, res)=> {
     const quote = data[Math.floor(Math.random() * data.length)];
     res.json(quote);
   });
  </code>
</details>


---

## VI. Homework Requirements
- Add a `quotes/recent` route that returns the last quote in the `data` array as JSON
  - test it with --> http://localhost:3000/quotes/recent
- Move the `/helloJSON` and `/timeJSON` routes over to a new route file named **api.js**
  - **api.js** will be in the **routes/** folder
  - in **app.js** you will need to  require() and `use()` **api.js** as we did with the other routes
  - when you are done, the new routes can be tested at:
    - http://localhost:3000/api/helloJSON
    - http://localhost:3000/api/timeJSON
  - be sure to update the button code in **rich-client.html** to work with these 2 new routes!
- **rich-client.html**:
  - add a functional "Show random quote" button that calls `/quotes/random`
    - display the values of the `content` and `author` properties
  - add a functional "Show most recent quote" button that calls `/quotes/recent`
    - display the values of the `content` and `author` properties
  - Optionally, think about D.R.Y. ("Don't Repeat Yourself") on your code whenever possible:
    - rather than 4 button callback functions, how about 2? I called mine `simpleFormatter` and `quoteFormatter`
    - *Closures* could help? - https://javascript.info/closure
    - *Curried* functions?  - https://javascript.info/currying-partials
  
---

## VII. Test all your routes!
- Staticly served files:
  - http://localhost:3000/rich-client.html
  - http://localhost:3000/spongegar.png
  - http://localhost:3000/404.html
- Your `express.Router()` routes:
  - http://localhost:3000/ - "hello" page
  - http://localhost:3000/bye - "bye" page
  - http://localhost:3000/quotes/ - array of all quotes
  - http://localhost:3000/quotes/random - one random quote
  - http://localhost:3000/quotes/recent - last quote in array
  - http://localhost:3000/api/helloJSON
  - http://localhost:3000/api/timeJSON
- The "File not found" `404` page --> http://localhost:3000/querty

---

## VIII. Homework Submission
- ZIP and POST the entire folder to the myCourses dropbox:
  - don't neglect to delete the **node_modules** folder BEFORE zipping
  - there is no need to post this to GitHub or Heroku

---

## IX. Screenshot of completed version

![screenshot](_images/express-1.png)

---

## X. Links
- https://expressjs.com/en/api.html#express.router

---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**6 - Intro to express**](6-intro-to-express.md)  |  [**IGME-430**](../) | [**8 - Passing params to express**](8-passing-params-in-express.md)
