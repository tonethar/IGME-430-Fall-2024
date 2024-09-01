# Read/Update/Delete with `json-server`

## I. Overview
- Do you know about the CRUD acronym?
  - **C**reate
  - **R**ead
  - **U**pdate
  - **D**elete
- We are going to learn about all of these today!

---

## II. HTTP Verbs 
- **C**reate - POST (create a resource)
- **R**ead - GET
- **U**pdate - PUT (usually used to completely replace resource), PATCH (partially update a resource)
- **D**elete - DELETE

---

## III. GET & POST Endpoints
### GET
- we covered these [last time](4-http-methods-with-json-server.md#GET-endpoints)

### POST
- Used to *create* a new resource
  - You can't do it from the Browser's *location box* (those are GET requests only)
  - You'll instead need to use an HTML `<form>` of `method="POST"` OR
  - You can use XHR or fetch() and set the request method to `POST`
  - You can use Postman!
    - POST http://localhost:3000/quotes
    - Under the request body tab, and with the "raw" radio button selected, add this JSON:

```json
{
  "index": null,
  "id": "80ba8ef9-f9a7-4459-a4a0-c1619ea7dafa",
  "author": "Oscad Wilder",
  "content": "The meaning of life is to party, hardy!",
  "tags": ["apocryphal"],
  "createdAt": null,
  "updatedAt": null
}
```

- Now click the "Send" button
  - You should get a response from the server, with a "201 Created" Status Code
 
---

**Before:**

![screenshot](_images/json-server-1.png)


**After:**

![screenshot](_images/json-server-2.png)

---

- Why did json-server send back the JSON object we created? According to the specification about `POST` - *"If a resource has been created on the origin server, the response SHOULD be 201 (Created) and contain an entity which describes the status of the request and refers to the new resource..."*
- BTW - you can generate new UUID's in the browser with `crypto.randomUUID()`

### Did our POST request work?
- Check http://localhost:3000/quotes and verify that the quote was created
- Open up the **quotes-data-2.json** file - you'll see that it has been updated and now contains the quote
- Fire up the **quotes-app-3/** client app and hit the "random" button a few times - at some point you should view the new quote

---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**4 - Exploring HTTP methods with json-server**](4-http-methods-with-json-server.md)  |  [**IGME-430**](../) | TBA
