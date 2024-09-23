# 6 - Intro to `express`

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

***BTW - we haven't created a `"start":...` script yet because ... we don't plan on deploying this to Heroku, until later ...***

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
  console.log(`App running on http://localhost:${port}`);
});
```

---

2) Type `npm run dev` (if the server is not already running)

- You should see `App running on localhost:3000` in the console
- In your browser, head to http://localhost:3000 to see `Hello World!` in the window
- See code explaination here: https://www.tutorialspoint.com/expressjs/expressjs_hello_world.htm

---

3) ***YOU DO THIS*** - add a  `/bye` endpoint (`GET` method) that prints `Goodbye!` in the console

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
// put this AFTER we instantiate `app`, and BEFORE our GET and POST routes
app.use(express.static('client'));
```

---

BTW - `app.use()` defines a "middleware" function - we'll get deeper into this later on in the course - see links at the top of this document for more info.

---

- Next, create a **client** folder (at the "top level" where **src** is)
  - then add these 3 files to it --> [intro-express-files](_files/intro-express-files/)
- Verify that the static files are  visible:
  - http://localhost:3000/rich-client.html
  - http://localhost:3000/spongegar.png
  - http://localhost:3000/404.html
- We only needed one line of code to do this! Easy Peasy! 

---

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
- Test the endpoint: http://localhost:3000/helloJSON
- When you are done wring code in **rich-client.html**, you should be able to click the button and see `Hello there!` in the `<div>`

---

## V. Showing a "404 File Not Found" message

1) Really easy! Add a "wildcard route" - basically a fallthrough - that matches any path not matched by earlier code.
- Put this code AFTER all of the other routes in **app.js**, and right before `app.listen(...)`

---

```js
// .all refers to ALL http methods - GET, POST, DELETE etc
// note .status(404) and method chaining
// .status(404) is how we send the 404 - File Not Found status code
app.all('*', (req, res) => {
  res.status(404).send('<h1>404! Page not found</h1>');
});
```

---

- **All of your previous routes should still work:**
  - http://localhost:3000
  - http://localhost:3000/bye
  - http://localhost:3000/helloJSON
  - http://localhost:3000/rich-client.html
  - http://localhost:3000/spongegar.png
  - http://localhost:3000/404.html
- And any other route not matched above should send you to the `404` "page" (Look under the Network tab to all see the `404` status code)
  - http://localhost:3000/page1
  - http://localhost:3000/qwerty

---

- **Want to show the 404.html page instead? Easy!**
  - replace the previous wildcard code with this:

```js
app.all('*', (req, res) => {
  res.status(404).sendFile(filePath404Page);
});
```

- You will also need to define `filePath404Page` - add the following to somewhere near the top of **app.js**

```js
const path = require('path');
const filePath404Page = path.resolve(__dirname,'../client/404.html');
```

- Test it with - http://localhost:3000/qwerty - you should now see the 404.html error page!

---

## VI. Updating nodemon

- One more thing - let's update `nodemon` so that it reboots our server whenever there are changes to any HTML or CSS files in the `client/` folder. Here's the new value for the `"dev"` key in **package.json**:

```json
"dev": "nodemon -e js,html,css,json ./src/app.js"
```

- You might have guessed that the `-e` flag stands for "file extensions we watch to watch"
- Test this by modifying **server.js** and saving the change - you should still see a server reboot
- Now modify one of the HTML files and save the change - you will now see a server reboot
- And now any changes to **package.json** will also cause a server reboot

---

## VII. Discussion & Reference
- We've given you a taste of what express can do
- You wrote dramatically less code than we did for *HW - Simple HTTP Server*
- And picked up a new capability - the custom 404 page
- Express response methods:
  - `res.send()` - Send data
  - `res.sendFile()` - Send a file
  - `res.json()` - Send JSON data
  - `res.status()` - Specify HTTP response code
  - `res.redirect()` -  Redirect to a certain path
  - `res.render()` -  Render and send a view template
- Hello World:
  - https://expressjs.com/en/starter/hello-world.html
- Routing:
  - https://expressjs.com/en/starter/basic-routing.html
- Serving static files:
  - https://expressjs.com/en/starter/static-files.html
  - https://expressjs.com/en/api.html#express.static
- Examples:
  - https://expressjs.com/en/starter/examples.html

---

## VIII. HW & Submission
- Add a `/timeJSON` endpoint to **server.js** that returns the current time in the JSON format
  - we previously did this in *3 - HW - Simple HTTP Server*
  - test this endpoint in the browser to be sure it works right - http://localhost:3000/timeJSON
- Add a button and code to **rich-client.html** that calls `/timeJSON`, and then displays the results in the browser window
  - we previously did this in *4 - Simple HTTP Server - add an Ajax client*
- Rubric:
  - (-2) each missing endpoint
  - (-2 each) "Hello" or "Time" button does not work
  - (-2) HTML error page does not work
- ZIP and POST the entire folder to the myCourses dropbox:
  - don't neglect to delete the **node_modules** folder BEFORE zipping
  - there is no need to post this to GitHub or Heroku
 
---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**5 - Streaming Media HW**](5-streaming-media.md)  |  [**IGME-430**](../) | [**7 - Express Routing**](7-express-routing.md)
