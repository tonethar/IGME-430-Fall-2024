# 6 - Intro to express

## I. Overview of express
- *Fast, "unopinionated", minimalist web framework for node:*
  - https://www.npmjs.com/package/express
  - http://expressjs.com/
- Considered the defacto package for Node.js and apps that utilize HTTP, routing and server-side view rendering 
- Has easy hooks for *middleware*:
  - https://expressjs.com/en/guide/using-middleware.html
  - https://expressjs.com/en/resources/middleware.html

---

## II. Get started!

1) Create a folder named **first-express-app** and `cd` into it

2) Create **package.json** and install some packages

    - `npm init -y`
    - `npm i express`
    - `npm i -D nodemon`

3) In **package.json**, verify that `"dependencies"` and `"devDependencies"` have the values you expect
   
4) Add the following to the "scripts" key of **package.json**
    - `"dev": "nodemon src/app.js"`

5) Create a **src** folder for your program files

6) Create **app.js** and put it in your **src** folder

7) Add `console.log('First Express');` to the top of **app.js**

8) `npm run dev` to test your code

9) Make a change to the code in **app.js** and save it - you should see that nodemon has detected the change and rebooted the server (**app.js**)

---

## III. How about some express?

1) Delete the `console.log`, and add the following to the top of **app.js**

```js
const express = require('express');

const port = 3000;

const app = express();

app.get('/', (req, res) => {
  res.send('Hello world!');
});

app.listen(port, () => {
  console.log(`App running on localhost:${port}`);
});
```

---

2) `npm run dev` (if the server is not already running)

- you should see `App running on localhost:3000` in the console
- in your browser, head to http://localhost:3000/ to see `http://localhost:3000/` in the console
- see code explaination here: https://www.tutorialspoint.com/expressjs/expressjs_hello_world.htm

---

3) ***YOU DO THIS*** - add a `/bye` endpoint that prints `Goodbye!` in the console

- test it with: http://localhost:3000/bye

5) You should have 2 `GET` endpoints at this point - which are easy to test in the browser. Let's add a POST endpoint:

```js
app.post('/addComment', function(req, res){
   res.send("You just called the post method at '/addComment'!\n");
});
```

- In your web browser, head to http://localhost:3000/addComment
  - This gives you a `not found` message in the browser, and if you check the n=browser Network inspector you'll see you also got a 404 status code
  - Why? Because requests sent in the browser's location box are always `GET`
  - To test this endpoint, launch Postman, choose the `POST` method, and try the above URL again. You should see the expected server response now.
