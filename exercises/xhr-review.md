# XHR Review

## I. Overview

- As a way to review JS and the browser DOM, we'll build a simple app that displays a random quote loaded from a JSON file

---

## II. Start Files

---

## III. Instructions
GOAL: To get the basics of this working
1. When the "Get a random quote!" button is clicked, show a quote!
  - the `id` of the button is `"btn-random"`
  - the `id` of the `<div>` where you can put the quote is `"content"`
  - the data file of quotes is located at `data/quotes-data.json`
  - use the `XMLHttpRequest` (aka `XHR`) object to download the JSON data
  - once the JSON file is loaded, use `JSON.parse()` to convert it to an object you can parse
  - show both the `.content` and `.author` of the quote to the user by creating a `<p></p>` and inserting it into the content `<div>`

2. **Error Handling A** - if a "404" (file not found) .status code happens, log a message to the console and notify the user.
Test this by changing the value of `jsonUrl` to "data/quotes-dataXYZ.json"

3. **Error Handling B** - if the loaded file does not parse to legal JSON (signified by JSON.parse() throwing an exception), log the exact error message to the console and notify the user.
  - You will need to use a `try`/`catch`/`finally` block.
  - Test this by changing the value of `jsonUrl` to "data/quotes-data.csv" (CSV doesn't parse to JSON)

4. Change the quote HTML (the `<p>...</p>` tag) to instead use the "card" HTML (that is commented out in the HTML file)

---

## IV. N.B.

1. Here, xhr.open's first parameter is "GET" - which is an HTTP protocol *method*
Other HTTP methods (for creating, updating and deleting resources) that we will use in the course include POST, PUT, PATCH and DELETE
2. Code style:
  - the "cool kids" pretty much exclusively use arrow functions these days
  - and template strings  (e.g. `Hello ${name}`) instead of string concatenation (e.g. "Hello " + name)
  - and destructured function parameters - try doing that somewhere
3. XHR has the ability to specify *request headers* (which are meta data about the request, and also a part of the HTTP protocol):
setRequestHeader(header, value)
example (which tells the server "Send me JSON if you can!"): xhr.setRequestHeader("content-type", "application/json")
