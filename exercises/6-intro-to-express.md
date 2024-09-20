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
   
4) Add the following to the `"scripts"` key of **package.json**
    - `"dev": "nodemon src/app.js"`

5) Create a **src** folder for your program files

6) Create **app.js** and put it in your **src** folder

7) Add `console.log('First Express');` to the top of **app.js**

8) Type `npm run dev` to test your code

9) Make a change to the code in **app.js** and save it - you should see that nodemon has detected the change and rebooted the server (**app.js**)

***BTW - we haven't created a `"start":...` script yet because we don't plan on deploying this to Heroku, yet...***

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

2) Type `npm run dev` (if the server is not already running)

- You should see `App running on localhost:3000` in the console
- In your browser, head to http://localhost:3000 to see `Hello World!` in the window
- See code explaination here: https://www.tutorialspoint.com/expressjs/expressjs_hello_world.htm

---

3) ***YOU DO THIS*** - add a `/bye` endpoint that prints `Goodbye!` in the console

- Test it in the browser here: http://localhost:3000/bye

---

4) You should have 2 `GET` endpoints at this point - which are easy to test in the browser. Let's add a POST endpoint with `app.post()`:

```js
app.post('/addComment', function(req, res){
   res.send("You just called the post method at '/addComment'!\n");
});
```

- In your web browser, head to http://localhost:3000/addComment
  - This gives you a `Cannot GET /addComment` message in the browser, and if you check the browser's Network inspector you'll see you also got a `404` status code. Express does this for us automatically with unknown endpoint requests (but very soon, we'll create our own custom "File not found" `404` message)
  - Why? Because requests sent in the browser's location box are always `GET`
  - To test this `POST` endpoint, launch the *Postman* app
    - create a new request
    - choose the `POST` method
    - try the above URL again
    - you should see the expected server response now!

---

## IV. Serving Static Files

- Recall that in recent assignments we've had to write specific endpoints for static files like **client.html**, **rich-client.html** and **dankmemes.png** etc?
- express can serve up static files for us, automatically, if we just tell it which folder to use
- add the following to **app.js**:

```js
// put this after we instantiate `app`
app.use(express.static('public'));
```

- Next, create a **public** folder (at the "top level" where **src** is)
  - then add these 2 files to it --> [intro-express-files](_files/intro-express-files/)
- Verify that the static files are  visible:
  - http://localhost:3000/rich-client.html
  - http://localhost:3000/spongegar.png
- Easy Peasy! 

***\*\* YOU DO THIS: \*\**** 
1) Modify the `<img>` tag in **rich-client.html** so that **spongegar.png** is displayed

2) In **app.js**, implement a `/helloJSON` endpoint that **rich-client.html** will be able to call when the button is clicked:

- It should return a status code of `200`, a `Content-Type` of `application/json`, and some JSON that looks like this:

```json
{
  "message": "Hello there!"
}
```

- Fortunately, `res.json()` does most of this for you!
  - give it an object, and it will stringify it for you
  - it will also send the correct `Content-Type`
- When you are done, you should be able to click the button and see `Hello there!` in the `<div>`

---

## V. Showing a "404 File Not Found" page

1) XX
