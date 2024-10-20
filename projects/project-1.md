# Project 1

## I. Overview
- Web APIs are ubiquitous in the modern world as a means of accessing and interacting with a dataset. Commonly, companies provide APIs to provide limited or complete access to the data they have and manage. Many of these APIs are publicly available such as the Google Maps API, Spotify API, PokeAPI, and many others. They allow other developers to build rich web applications and experiences that are augmented by the data they get. Private Web APIs are also used by nearly every company to pass data between various internal systems and tools.
- *For this project, you will not be utilizing one of these pre-existing APIs. Instead, you will take a JSON dataset and create a Web API that allows others to access, search, filter, and edit your dataset.*

---

## II. Files
- [430 Project 1 Datasets.zip (ZIP)](_files/430%20Project%201%20Datasets.zip) 

---

## III. Code Requirements
- You should have already completed the [Project 1 - "Get Going!" Checkpoint](project-1-checkpoint.md)
- We will be utilizing the [express](https://www.npmjs.com/package/express) library (on top of node's built-in [http](https://nodejs.org/api/http.html))
- All client-side code will be written as we have done so in 330/430 (arrow functions, `const` & `let` but NO `var`, modern JS features such as destructuring where possible, etc)
- Server code will pass `npm test`
- Other (should all be present from completing the project 1 checkpoint):
  - Uses Git for version control in a repo that the professor can access
  - Uses ESLint with the Airbnb spec for all server code
  - Uses GitHub Actions for build testing
  - Uses correctly formed **.eslintrc** file and **.gitignore** files
  - Uses a cloud service (such as Heroku) for deployment
  - Borrowed code and code fragments MUST be credited in code comments AND in the written documentation for the project:
    - you do not have to document any code I gave you in class or on the assignments
  - Separation of Concerns: your code should be appropriately broken up into files and functions based on the main functionality of those pieces of code:
    - you must utilize public functions  **p1-db.js** for all data access, queries, filtering etc
  - **D.R.Y.** - **D**on’t **R**epeat **Y**ourself. If you have multiple nearly identical blocks of code, those should be factored out into separate functions.
  - Code must be well commented. You don’t need to comment on every line. Have a comment for each function, and comments for confusing lines of code. Ideally, code should be "self-documenting", meaning the variable and function names explicitly state what they are and what they do
  - Code must be free of runtime and ESLint errors

---

## IV. Documentation
- You are required to submit documentation of how you met all of the requirements
  - this can be submitted separately as a DOC or PDF, or you could create a **README.md** file in your private project repo

---

## V. `GET` endpoints

### V-a. Array of ALL resources - `/api/countries`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/countries

### V-b. One random resource - `/api/country/random`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/random

### V-c. Most recently added resource - `/api/country/recent`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/recent

### V-d. `/api/country/:id`
- Hint: use `req.params` as we did in **quotes.js**
  - [Part VIII. Accessing parameters via the *route*](../exercises/8-passing-params-in-express.md#v-accessing-parameters-via-the-route)
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/AUS - SUCCESS
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/GTM - SUCCESS
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/GTA - return "no id match found" error message and a `404` status code ("Not Found")
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/ - if no `id` is passed in, don't search the database, and return a "id is required" error message and a `400` status code ("Bad Request")

### V-e. `/api/country/?name=`
- Hint: use `req.query` as we did in **quotes.js**
  - [Part VIII. Accessing *query string* parameters with express](../exercises/8-passing-params-in-express.md#iv-accessing-query-string-parameters-with-express)
- Have the router do `.trim()` on the search string that is passed in
- The DB must do a *case insensitive* search
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/?name=albania - SUCCESS
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/?name=AlbaniA - SUCCESS
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/?name=Latveria - return "no name match found" error message and `404` status code ("Not Found")
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/?name= - if the string is empty don't search the database, and return a "value for name is required" error message and `400` status code ("Bad Request")
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
- Placeholder index page links:
  - https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/
  - https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/index.html

### V-g. admin.html
- We covered most of this here: [Improved admin `<form>`](p1-improved-admin-form.md)
- This will be stored in your **client/** folder and served by express (via `app.use(express.static('client'))`)
- This page will provide a way for an *administrator* to interact with your API with `DELETE`, `POST` and `PUT` requests as we did with the hoot's **admin.html**
- **admin.html** will:
  - consist of [valid HTML](https://validator.w3.org/) & [valid CSS](https://jigsaw.w3.org/css-validator/)
  - will allow the user to *interact with ALL* of `DELETE`, `POST` and `PUT` endpoints of your API that are required *below*
  - will *look nothing like* the **admin.html** pages from our exercises
  - will be *nicely styled* with CSS, the page aesthetics at a minimum should be "not ugly"
  - will perform ***client-side validation*** of operations with JS - for example, if a required input field is empty when the user clicks a search button, don't send the search to your API server, and let the user know what the error is
  - will be *usable* and give hints to the user where necessary:
    - make `DELETE`ing a resource easier - the admin should be able to search for a resource by name and then delete it. They should NOT (for example) have to copy/paste an `id` value from another part of the UI
    - ditto for `PUTing` edits to the server
    - this easiest way to do this is to utilize a `type="hidden"` `<input>` field - https://www.w3schools.com/tags/att_input_type_hidden.asp
    - I will give you some more hints about this AFTER the break
- Placeholder admin page link: https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/admin.html

### V-h. 404 page
- All other get endpoints (not located under the `/api` route) will be served a `404` status code and an HTML error page
  - ex. https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/xyz 

---

## VI. `HEAD` endpoints
- We covered this here: [Express and responding to HEAD requests](p1-express-HEAD.md)
- These will be tested with Postman
- Choose a minimum of 3 GET endpoints that will also respond to `HEAD` requests
- The following 3 headers will be sent:
  - `Content-Type` - specifying the actual MIME content type that is being returned
  - `Content-Length` - specifying the actual content length in bytes
  - `X-Coder` - a custom header specifying your initials
- Here's an example you can try in Postman - `HEAD` https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/countries/

---

## VII. XML endpoint
- We covered this here: [`Accept` headers and XML](p1-accept-header-xml.md)
- This will be tested with Postman
- Choose 1 GET endpoint that will return XML when the `Accept: application/xml` header is sent by the client
- Here's an example you can try in Postman with `GET` and the `Accept: application/xml` header - https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/countries/

---

## VIII. `DELETE`, `POST` and `PUT` endpoints
- Implement these as we did in the "hoots" exercise - you can name these endpoints as you wish:
  - as we did in "hoots", primarily utilizing a query string OR
  - more analagous to how `json-server` named them
- Unlike the "hoots" exercise, you will need to implement some level of ***server-side validation***
- Return appropriate "success" status codes along with the resource - e.g. `200`, `201`
- Return appropriate "error" status codes along with a JSON error object - e.g. `400`, `404`
- `DELETE`
  - on success, return JSON with the `id` of the resource that was deleted (and/or the entire resource, it's up to you) and a `200` status code
  - on failure, return "no resource found!" JSON and a `400` status code
- `POST`
  - You do NOT have to send ALL of the required resource fields to the server, instead, have the server initialize the resource's unique `id` and any other fields that can be initialized to a default value
  - on success, return the newly created resource as JSON and a `201` status code
  - on failure, return "missing required fields" JSON and a `400` status code
- `PUT`
  - You are only required to make 3 of the resource's fields "editable"
  - `id` is unique, don't make that editable
  - on success, return the newly updated resource as JSON and a `200` status code
  - on failure, return "no id match found" JSON and a `400` status code

---

## IX. "Above and Beyond"
- Doing all of the above perfectly gets you a 90% - to get higher, you need to add some extra features or polish to the app
- Ideas:
  - *name* search returns an array of matches, not necessarily just the first match
  - utilize the query string to add filtering and/or sorting capabilities
  - another `/api/` endpoint that does something useful? 
  - excellent page design, usability or new features? on **index.html** and/or **admin.html**

---

## X. Submission

### X-a. Delete ALL unneeded code and files
- Be sure to get rid of ALL unneeded code (ex. **quotes.js**) and files (ex. **spongegar.png**, **rich-client.html** etc)


### X-b. Links (to be provided in Documentation)
- `GET` endpoints (see examples running on Heroku, above)
  - Array of ALL resources
  - One random resource
  - Most recently added resource
  - One resource found by id
  - One resource found by name - exact match search
  - One resource found by name - case insensitive search
  - One resource found by name - bad name - returns a `404` JSON object
  - One resource found by name - empty string for name - returns a `400` JSON object
  - Limk to **index.html**
  - Link to **admin.html**
  - Link to **404.html**
- `HEAD` endpoints that return the required headers
  - list all 3 supported endpoints
- `XML`
  - give the one supported endpoint
- `DELETE`
  - give the one supported endpoint
- `POST`
  - give the one supported endpoint and describe the required fields in the JSON data that is passed over (ex. The `content` property is required)
- `PUT`
  - give the one supported endpoint and describe the required fields in the JSON data that is passed over (ex. The `content` property is required)


### X-c. Documentation
- In PDF or DOC format, or as a README.md file in your repo
- Provide ALL links in section X-b. above - and where possible give a "working" link (as was done for you in section V. above) that provides a valid response
- Describe:
  - what went right with this project
  - what went wrong with this project
  - what did you learn while completing this project
  - what code fragments did you use or borrow? List these here, and make sure that there is also a comment and/or link in the source code
  - detail your "Above and Beyond" work that

### X-d. Submission
- In the myCourses dropbox and/or comments field
  - provide a link to your project 1 GitHUb repo
  - a ZIP of your source code (without the **node_modules** folder

### X-e. Rubric
- 90% is the base grade
- (**+0% to +20%**) for documented "Above and Beyond" work
- (-5%) for each missing or non-functional endpoint (or an endpoint that does not send the correct status code)
- (-15%) **client.html** requirements not met
- (-25%) **admin.html** requirements not met
- (-2%) each `npm test` error
- (-10%) Documentation not complete
- (-1% to 10%) "Back end" checkpoint was not complete
- (-TBD%) unnecessary code or files, code errors, other missing requirements or violations of coding standards
