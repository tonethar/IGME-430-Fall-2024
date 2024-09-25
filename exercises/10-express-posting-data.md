# 10 - `POST`ing data to express

- We have seen how to pass data to an express app with `GET` via URL params and URL routes ...
- now let's see how to send data to express via `POST`

---

## I. Create the GET `/api/hoots` endpoint

- `/api/hoots` will be an endpoint where we can play around with the `GET`, `POST`,`DELETE` and `PATCH` HTTP methods
- "hoots" will be short declamations or interjections, such as "Yay! Free lunch is good" or "Hmm... Birds aren't real!"
- Here's the code for our array of `hoots` that has a single default hoot - add this to  **routes/api.js**

```js
const generateNewId = () => crypto.randomUUID();

const hoots = [{
  id: generateNewId(),
  content: "Let's Rock!",
  createdAt: new Date(),
}];
```

- ***\*\* YOU TRY THIS \*\**** --> Now add a route to **routes/api.js** that will display all of the `hoots` as JSON - it will be avaialble at **/api/hoots**

<details>
  <summary><b>Solution for <kbd>/api/hoots</kbd> in index.js</b></summary>
  <code>
   router.get('/hoots', (req, res) => {
    res.json(hoots);
   });
  </code>
</details>

- Test it at: http://localhost:3000/api/hoots

---

## XX. Reference
- https://www.digitalocean.com/community/tutorials/use-expressjs-to-get-url-and-post-parameters#step-5-using-req-body-with-post-parameters


---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**9 - Putting our project on Heroku**](9-putting-project-on-heroku.md)  |  [**IGME-430**](../) | 11 - More POSTing
