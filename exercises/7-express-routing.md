# 7 - Express Routing

## Overview
- *Routing* refers to determining how an application responds to a client request for a particular endpoint
- *Routing libraries* make it easy to organize your app's *routes* - for example `/home`, `/quotes`, `/quotes/id`, `quotes/random`, `quotes/random/5` etc
- We are going to re-architect **first-express-app** to use a routing library

---

## I. Get Started
- Duplicate the entire **first-express-app** folder and re-name the copy to **first-routing-app**
  - you might want to delete the **node_modules** folder before you make the copy; if so, don't forget to `npm i`
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
  - `/`, `/bye`, `helloJSON`, etc endpoints will no longer function and will give the `Cannot GET` message 

---

## III. Adding the router
- Inside your **src/** directory, create a **routes** directory
- Inside of **src/routes/**, create a **index.js** file
- Make **index.js** look like this:

---

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
- To utilize these routes, add the following to **app.js**:

---

```js

// import routes (put this near top)
const indexRouter = require('./routes/index.js');

// use routes (put this near the bottom, BEFORE app.listen()
app.use('/', indexRouter);

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

---



---
## XX. Links
- https://expressjs.com/en/api.html#express.router
