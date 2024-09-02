# Read/Update/Delete with `json-server`

---

## Overview

[I. CRUD](#i-crud)

[II. CRUD & HTTP Methods](#ii-crud--http-methods-aka-verbs-actions-etc)

[III. `GET` & `POST` Endpoints](#iii-get--post-endpoints)

[IV. `DELETE`](#iv-delete)

[V. `PATCH`](#v-patch)

[VI. `POST` in the browser with an HTML `<form>`](#vi-post-in-the-browser-with-an-html-form)
 
  
---

## I. CRUD
- Do you know about the CRUD acronym?
  - **C**reate
  - **R**ead
  - **U**pdate
  - **D**elete
- We are going to learn about how to implement all of these in HTTP, today!

---

## II. CRUD & HTTP Methods (aka "verbs", "actions", etc)
- **C**reate - `POST` (create a resource)
- **R**ead - `GET`
- **U**pdate - `PUT` (usually used to completely replace resource), `PATCH` (partially update a resource)
- **D**elete - `DELETE`

---

## III. `GET` & `POST` Endpoints
### `GET`
- we covered these [last time](4-http-methods-with-json-server.md#GET-endpoints)

### `POST`
- Used to *create* a new resource
  - You can't do it from the Browser's *location box* (those are GET requests only)
  - You'll instead need to use an HTML `<form>` of `method="POST"` OR
  - You can use XHR or fetch() and set the request method to `POST`
  - You can use Postman!
    - `POST` http://localhost:3000/quotes
    - Under the request body tab, and with the "raw" radio button selected, add this JSON:

```json
{
  "index": null,
  "id": "80ba8ef9-f9a7-4459-a4a0-c1619ea7dafa",
  "author": "Oscad Wilder",
  "content": "The meaning of life is to party, hardy!",
  "tags": ["uncategorized"],
  "createdAt": null,
  "updatedAt": null
}
```

- Now click the "Send" button
  - You should get a response from the server, with a "201 Created" Status Code
 
---

**Before:**

![screenshot](_images/json-server-1.png)


**After the server responds:**

![screenshot](_images/json-server-2.png)

---

- Why did json-server send back the JSON object we created?
  - according to the specification about `POST` - *"If a resource has been created on the origin server, the response SHOULD be 201 (Created) and contain an entity which describes the status of the request and refers to the new resource..."*
- BTW - you can generate new UUID's in the browser with `crypto.randomUUID()`

### Did our POST request work?
- Check `GET` http://localhost:3000/quotes both in the browser and in Postman, and verify that the quote was created
- Open up the **quotes-data-2.json** file - you'll see that it has been updated and now contains the quote
- Fire up the **quotes-app-3/** client app and hit the "random" button a few times - at some point you should view the new quote

---

## IV. `DELETE`
- To delete a resource, we can pass in the `id`
  - the following will delete the Oscar Wilde quote:
  - `DELETE` `http://localhost:3000/quotes/4c951b60-1f90-41e7-a913-c1f454ff4c6e`

**Before:**

![screenshot](_images/json-server-3.png)

**After:**
- The server responds with a status code of `200 OK`
- The Oscar Wilde quote is GONE!
- Attempting to `DELETE` a resource that isn't there returns a `404 Not Found` status code

---

## V. `PATCH`

- Used to update existing resources
- You need to send over (just) the changes in the Body (like we did with `POST`), select "raw", and "JSON"
- `PATCH` `http://localhost:3000/quotes/7690718f-01b7-4775-9998-6a4adb480d27`
- Body text - `{"author": "Dr. Thomas Sowell"}`

![screenshot](_images/json-server-4.png)

- In the example above, we added "Dr." to the beginning of Thomas Sowell's name. The server returned the updated resource.

---

## VI. `POST` in the browser with an HTML `<form>`

- Let's build an admin form to perform Create, Read, and Delete operations

**quotes-admin-start.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Quotes Admin</title>
</head>
<body>
  <h1>Quotes Admin</h1>
  <h2>Add a Quote (POST)</h2>
  <!-- AI prompt - "I need an HTML form with content, author and id fields" -->
  <!-- Nice Reference: https://www.w3schools.com/html/html_forms.asp -->
  <form
    id="form-new-quote"
    action="http://localhost:3000/quotes" 
    method="POST" 
  >
    <label for="content">Quote:</label><br>
    <textarea id="content" name="content" rows="4" required></textarea><br><br>
    
    <label for="author">Author:</label><br>
    <input type="text" id="author" name="author" required><br><br>
    
    <label for="id">ID:</label><br>
    <input id="id" name="id" required size="38" readonly><br><br>
    
    <input type="submit" value="Submit">
</form>

  <hr>

  <h2>POST Results</h2>
  <div id="post-results">
    <p></p>
    <pre></pre>
  </div>

  <hr><hr>

  <h2>Delete Quote</h2>
  <button id="btn-delete">Delete</button> | <input id="delete-id" size="38"> 

  <h3>DELETE Results</h3>
  <div id="delete-results">
    <p></p>
    <pre></pre>
  </div>

  <hr><hr>

  <h2>View All Quotes</h2>
  <div id="all-quotes"></div>
  <script>
    // Code goes here!
  </script>
  </body>
  </html>
```


---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**4 - Exploring HTTP methods with json-server**](4-http-methods-with-json-server.md)  |  [**IGME-430**](../) | TBA
