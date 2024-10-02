# 15 - Errata & Notes

## I. Questions

### I-A. Routes ([in part 8](8-passing-params-in-express.md#v-accessing-parameters-via-the-route))
- Explain the difference betweeen these routes, which are located in **routes/api.js**:
  - `router.get('/id', (req, res)=>...)`
  - `router.get('/:id', (req, res)=>...)`
  - `router.get('/:id([0-9,a-z,A-Z,-]{36})', (req, res)=>...)`

---

### I-B. [`/addHoot`](10-express-posting-data.md#ii-b-adding-post-data-to-the-hoots-array) (in part 10)

- What is the statement on lines 28-30 called? What does it do?
- What do you think the server should do if no value for `content` is passed in?
  - A. Create an "empty" hoot OR
  - B. Return an error message

---

## I-C. [admin.html](11-post-admin-page.md#ii-adminhtml---add-a-hoot) (in part 11)
- Do you see any issues with the *request headers* being sent on lines 81 & 82?
- When is the *body* of the request actually sent?
  - A. At the beginning of the request before the request headers
  - B. In the middle of the request
  - C. At the end of the request
- Take a look at `addHootForm.onsubmit = ...` on line 131, and explain every line of code.
  - what does `evt.preventDefault()` do?
  - what does `addHootForm['content']` refer to?
  - what is the "long way" to write line 135?
  - what does line 137 do?
  - explain line 138. What is the value of `addHootCallback()`?
  
---

## I-D. [`DELETE` a hoot](12-delete-hoot-server-client.md) (in part 12)
- See line #67 & https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/DELETE
- What is the status code send back when a delete is successful?
- Other than the deleted hoot, what other content could (or should) be sent back as a response?
- Explain what line 154 does.

---

## I-E. [Edit (`PUT`) a hoot](13-put-a-hoot.md) (in part 13)
- The `router.put(...)` endpoint has a huge code problem - although it works it's breaking *encapsulation* - what is the exact issue?
- What should the code do if `content` is `undefined`?
- Which status code should be sent back if a `PUT` *fails*?
- Explain what line 169 does.

---

## I-F. 

