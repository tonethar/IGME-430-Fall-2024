# 10 - `POST`ing data to express

- We have seen how to pass data to an express app with `GET` via URL params and URL routes ...
- now let's see how to send data to express via `POST`

---

## I. Create the GET `/api/hoots` endpoint

- `/api/hoots` will be an endpoint where we can play around with the `GET`, `POST`,`DELETE` and `PUT` HTTP methods
- "hoots" will be short declamations or interjections, such as "Yay! Free lunch is good" or "Hmm... Birds aren't real!"
- Here's the code for our array of `hoots` - it has a single default hoot - add this code to  **routes/api.js**:

```js
const generateNewId = () => crypto.randomUUID();

const hoots = [{
  id: generateNewId(),
  content: "Let's Rock!",
  createdAt: new Date(),
}];
```

- ***\*\* YOU TRY THIS \*\**** --> Now add a `GET` route to **routes/api.js** that will display all of the `hoots` as JSON - it will be available at **/api/hoots**

<details>
  <summary><b>Solution for <kbd>/api/hoots</kbd> in routes/api.js</b></summary>
  <code>
   router.get('/hoots', (req, res) => {
    res.json(hoots);
   });
  </code>
</details>

---

- Test it at: http://localhost:3000/api/hoots - you should see the contents of the `hoots` array - as JSON
  
![screenshot](_images/express-4.png)

---

## II. Create the POST `/api/addHoot` endpoint
- `POST`ing in HTTP is for when we want to send data to the server - for example a new Hoot!
- To get started, add the following to **routes/api.js**:

```js
router.post('/addHoot', (req, res) => {
  const test = {
    testId: generateNewId(),
    testMsg: 'POST /api/addHoot - test',
  };
  res.json(test);
});
```

---

- If you head to http://localhost:3000/api/addHoot in the browser you'll be calling a `GET` endpoint that does not exist
  
![screenshot](_images/express-5.png)

---


- To properly test this `POST` endpoint, go ahead and use Postman to connect to http://localhost:3000/api/addHoot - and don't forget to set the method to `POST`
- Did you forget how to use Postman with `POST` requests? See --> [Week 2 - Read/Update/Delete with json-server](5-read-update-delete-json-server.md#iii-get--post-endpoints)
- If everything is working you should see something like this in the response body (although the `id` will be different everytime this is called):

![screenshot](_images/express-6.png)

---

- This `POST` `/addHost` endpoint isn't doing much yet:
  - it's *returning* some data
  - but not *accepting* any data
- So let's move on!

---

### II-A. Accessing `POST` data sent by the client
- Let's move on and add code that accepts data that is sent along with the `POST` request
- `request.body` is a property that contains any `POST` data that is sent with a `POST` request
- First make the two changes below in the `POST` `/api/addHoot` route:

```js
router.post('/addHoot', (req, res) => {
  console.log('req.body=', req.body); // NEW!
  const test = {
    testId: generateNewId(),
    testMsg: req.body.content, // NEW!
  };
  res.json(test);
});
```

- Over in **app.js** - you just need to add this one line of code, that tells express to handle `POST` JSON data:
  - put this right AFTER `app.use(express.static('client'));`

```js
// put this right AFTER `app.use(express.static('client'));`
app.use(express.json());
```

---

- In Postman, send a `POST` request to `http://localhost:3000/api/addHoot`
  - in the request body, make it type "raw" and JSON
  - here's the JSON you can send: `{ "content" : "This is a new Hoot!" }`
 
![screenshot](_images/express-7.png)

---

- Check the Node console - it will log:

```
req.body= { content: 'This is a new Hoot!' }`
```

- If we change the log to `console.log('req.body.content=', req.body.content);` we will instead see:

```
req.body.content= This is a new Hoot!
```

- Meaning that express is taking that string content that's coming over the `POST` request, and `JSON.parse()`ing it into an object for us!

---

### II-B. Adding `POST` data to the `hoots` array 


- Here's your new version of POST `/api/addHoot` (replace the old version with this one):

![screenshot](_images/express-12.png)

---

- In Postman, head to http://localhost:3000/api/addHoot and send the same request we did last time:
  - the one with the `{ "content" : "This is a new Hoot!" }` data

![screenshot](_images/express-8.png)

---

- In a browser, head to http://localhost:3000/api/hoots to see that the new hoot has been added to the array:

![screenshot](_images/express-9.png)

- If you head back to Postman and click the Send button a few more times, and then reload http://localhost:3000/api/hoots in the browser, you will see that more hoots have been added, each with a unique `id` value

---

- ***Oops! One little update to the code above - you may have already caught it - here we should be sending back an HTTP status code of `201 Created`, NOT `200 Ok`***
  - it's an easy fix! Change `res.json(hoot)` to `res.status(201).json(hoot);`
  - test it again in Postman to confirm you can see the `201` status code

--- 


## III. Reference
- https://www.digitalocean.com/community/tutorials/use-expressjs-to-get-url-and-post-parameters#step-5-using-req-body-with-post-parameters

---

## IV. Wrap up
- Notice how we are building out and testing these server capabilities *first*, *"server first"*, before we write any *client* code ...
- ... but now it's time to create a way for the user to interact with our app, so go ahead and move on to the next part!


---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**9 - Putting our project on Heroku**](9-putting-project-on-heroku.md)  |  [**IGME-430**](../) | [**11 - Creating admin.html**](11-post-admin-page.md)
