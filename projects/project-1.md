# Project 1 (DRAFT)

## I. Overview
- Web APIs are ubiquitous in the modern world as a means of accessing and interacting with a dataset. Oftentimes companies provide APIs to provide limited or complete access to the data they have and manage. Many of these APIs are publicly available such as the Google Maps API, Spotify API, PokeAPI, and many others. They allow other developers to build rich web applications and experiences that are augmented by the data they get. Private Web APIs are also used by nearly every company to pass data between various internal systems and tools.
- *For this project, you will not be utilizing one of these preexisting APIs. Instead, you will take a JSON dataset and create a Web API that allows others to access, search, filter, and edit your dataset.*

---

## II. Files
- [Project 1 Requirements (PDF)](_files/430%20Project%201%20(New%2C%202024).pdf)
- [430 Project 1 Datasets.zip (ZIP)](_files/430%20Project%201%20Datasets.zip) 

---

## III. Additional Requirements
- We will be utilizing the [express](https://www.npmjs.com/package/express) libary (in lieu of node's built-in [http](https://nodejs.org/api/http.html))

---

## IV. Example
- https://willoughby-project-1-5f0f90052f40.herokuapp.com/

---

## V. `GET` endpoints

### V-A. Array of ALL elements - `/api/countries`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/countries

### V-B. One random element - `/api/country/random`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/random

### V-C. Most recently added element - `/api/country/recent`
- https://p1-430-abc1234-b3dbd8e918a3.herokuapp.com/api/country/recent

### V-D. `/api/country/:id`
- Have the router do `.trim()` on the `id` in the path
- The DB must do a *case insensitive* search
- http://localhost:3000/api/country/AUS - SUCCESS
- http://localhost:3000/api/country/GTM - SUCCESS
- http://localhost:3000/api/country/GTA - return error message and `404` status code
- http://localhost:3000/api/country/%20 - if the string is empty don't search the database & return error message and `404` status code

### V-E. `/api/country/?name=`
- Have the router do `.trim()` on the search string that is passed in
- The DB must do a *case insensitive* search
- http://localhost:3000/api/country/albania - SUCCESS
- http://localhost:3000/api/country/AlbaniA - SUCCESS
- http://localhost:3000/api/country/Latveria - return error message and `404` status code
- http://localhost:3000/api/country/%20 - if the string is empty don't search the database & return error message and `404` status code

### V-X. index.html
- This will be stored in your **client/** folder and served by express (via `app.use(express.static('client'))`)

### V-XX. admin.html
- This will be stored in your **client/** folder and served by express (via `app.use(express.static('client'))`)

### V-XXX. 404 page
- All other get endpoints will be served a `404` status code and an HTML error page 

---

## VI. HEAD endpoints
- These will be tested with Postman
- Choose a minimum of 3 GET endpoints that will also respond to `HEAD` requests
- The following 3 headers will be send
  - `Content-Type` - specifying the actual MIME content type that is being returned
  - `Content-Length` - specifying the actual content length in bytes
  - `X-Coder` - a custom header specifying your initials
- Here's an example you can try in Postman - `HEAD` http://localhost:3000/api/hoots/

---

## VII. XML endpoints

---

## VIII. POST, DELETE and PUT endpoints

---

## IX. "Above and Beyond"
- Suggestions:
  - utilize query string to add filtering, so

---

## XX. Submission

### XX-A. links
- GET endpoints
  - Array of ALL elements
  - One random element
  - Most recently added element
  - One element found by name - exact match search
  - One element found by name - case insensitive search
  - One element found by name - bad name - returns a 404 JSON object
- HEAD endpoints
  - 





