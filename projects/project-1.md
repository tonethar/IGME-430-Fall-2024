# Project 1 (DRAFT)

## I. Overview
- Web APIs are ubiquitous in the modern world as a means of accessing and interacting with a dataset. Oftentimes companies provide APIs to provide limited or complete access to the data they have and manage. Many of these APIs are publicly available such as the Google Maps API, Spotify API, PokeAPI, and many others. They allow other developers to build rich web applications and experiences that are augmented by the data they get. Private Web APIs are also used by nearly every company to pass data between various internal systems and tools.
- *For this project, you will not be utilizing one of these pre-existing APIs. Instead, you will take a JSON dataset and create a Web API that allows others to access, search, filter, and edit your dataset.*

---

## II. Files
- [Project 1 Requirements (PDF)](_files/430%20Project%201%20(New%2C%202024).pdf)
- [430 Project 1 Datasets.zip (ZIP)](_files/430%20Project%201%20Datasets.zip) 

---

## III. Code Requirements
- We will be utilizing the [express](https://www.npmjs.com/package/express) libary (on top of node's built-in [http](https://nodejs.org/api/http.html))
- All client-side code will be written as we have done so in 330/430 (arrow functions, `const` & `let` but NO `var`, modern JS features such as destructuring where possible, etc)

---

## IV. Example
- https://willoughby-project-1-5f0f90052f40.herokuapp.com/

---

## V. `GET` endpoints

### V-a. Array of ALL resources - `/api/countries`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/countries

### V-b. One random resource - `/api/country/random`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/random

### V-c. Most recently added resource - `/api/country/recent`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/recent

### V-d. `/api/country/:id`
- Have the router do `.trim()` on the `id` in the path
- http://localhost:3000/api/country/AUS - SUCCESS
- http://localhost:3000/api/country/GTM - SUCCESS
- http://localhost:3000/api/country/GTA - return "no id match found" error message and a `404` status code ("Not Found")
- http://localhost:3000/api/country/ - if no `id` is passed in, don't search the database, and return a "id is required" error message and a `400` status code ("Bad Request")

### V-e. `/api/country/?name=`
- Have the router do `.trim()` on the search string that is passed in
- The DB must do a *case insensitive* search
- http://localhost:3000/api/country/?name=albania - SUCCESS
- http://localhost:3000/api/country/?name=AlbaniA - SUCCESS
- http://localhost:3000/api/country/?name=Latveria - return "no name match found" error message and `404` status code ("Not Found")
- http://localhost:3000/api/country/?name= - if the string is empty don't search the database, and return a "value for name is required" error message and `400` status code ("Bad Request")
- If your data source has multiple resources with the same *name* (or similar names), just return the first match

### V-f. index.html
- This will be stored in your **client/** folder and served by express (via `app.use(express.static('client'))`)
- This page will provide a way for an *end-user* to interact with your API
- **index.html** will:
  - consist of [valid HTML](https://validator.w3.org/) & [valid CSS](https://jigsaw.w3.org/css-validator/)
  - will allow the user to *interact with ALL* of the "Read Only" (`GET`) endpoints of your API that are required *above*
  - will *look nothing like* the **client.html** and **admin.html** pages from our exercises
  - will be *nicely styled* with CSS, the page aesthetics at a minimum should be "not ugly"
  - will be *usable* and give hints to the user where necessary (ex. *"Enter a country code - example 'AUS'"*)
  - will perform client-side validation of operations with JS - for example, if a required input field is empty when the user clicks a search button, don't send the search to your API server, and let the user know what the error is

### V-g. admin.html
- This will be stored in your **client/** folder and served by express (via `app.use(express.static('client'))`)
- This page will provide a way for an *administrator* to interact with your API with `DELETE`, `POST` and `PUT` requests as we did with the hoot's **admin.html**
- **admin.html** will:
  - consist of [valid HTML](https://validator.w3.org/) & [valid CSS](https://jigsaw.w3.org/css-validator/)
  - will allow the user to *interact with ALL* of `DELETE`, `POST` and `PUT` endpoints of your API that are required *below*
  - will *look nothing like* the **admin.html** pages from our exercises
  - will be *nicely styled* with CSS, the page aesthetics at a minimum should be "not ugly"
  - will perform client-side validation of operations with JS - for example, if a required input field is empty when the user clicks a search button, don't send the search to your API server, and let the user know what the error is
  - will be *usable* and give hints to the user where necessary:
    - make `DELETE`ing a resource easier - the admin should be able to search for a resource by name and then delete it. They should NOT (for example) have to copy/paste an `id` value from another part of the UI
    - ditto for `PUTing` edits to the server
    - this easiest way to do this is to utilize a `type="hidden"` `<form>` field - https://www.w3schools.com/tags/att_input_type_hidden.asp
    - I will give you some more hints about this AFTER the break

### V-h. 404 page
- All other get endpoints (not located under the `/api` route) will be served a `404` status code and an HTML error page 

---

## VI. `HEAD` endpoints
- We covered this here: [Express and responding to HEAD requests](p1-express-HEAD.md)
- These will be tested with Postman
- Choose a minimum of 3 GET endpoints that will also respond to `HEAD` requests
- The following 3 headers will be send
  - `Content-Type` - specifying the actual MIME content type that is being returned
  - `Content-Length` - specifying the actual content length in bytes
  - `X-Coder` - a custom header specifying your initials
- Here's an example you can try in Postman - `HEAD` http://localhost:3000/api/countries/

---

## VII. XML endpoint
- We covered this here: [`Accept` headers and XML](p1-accept-header-xml.md)
- This will be tested with Postman
- Choose 1 GET endpoint that will return XML when the `Accept: application/xml` header is sent by the client
- Here's an example you can try in Postman -

---

## VIII. `POST`, `DELETE` and `PUT` endpoints
- Implement these as we did in the "hoots" exercise
- Return appropriate "success" status codes along with the resource - e.g. `200`, `201`
- Return appropriate "error" status codes along with a JSON error object - e.g. `400`, `404`

---

## IX. "Above and Beyond"
- Doing all of the above perfectly gets you a 90% - to get higher, you need to add some extra features or polish to the app
- Ideas:
  - *name* search returns an array of matches 
  - utilize the query string to add filtering and/or sorting capabilities
  - excellent page design and usability on **index.html** and **admin.html**

---

## X. Submission

### X-a. links
- GET endpoints
  - Array of ALL resources
  - One random resource
  - Most recently added resource
  - One resource found by name - exact match search
  - One resource found by name - case insensitive search
  - One resource found by name - bad name - returns a 404 JSON object
  - One resource found by id
- HEAD endpoints that return the required headers
  - list all 3 supported endpoints

### X-b. Rubric
- (-5%) for each missing endpoint
- (-25%) **client.html** requirements not met
- (-25%) **admin.html** requirements not met



