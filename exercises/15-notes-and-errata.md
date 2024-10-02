# 15 - Errata & Notes

## I. Questions

### I-A. [`/addHoot`](10-express-posting-data.md#ii-b-adding-post-data-to-the-hoots-array) (in part 10)

- What is the statement on lines 28-30 called? What does it do?
- What do you think the server should do if no value for `content` is passed in?
  - A. Create an "empty" hoot OR
  - B. Return an error message

---

## I-B. [admin.html](11-post-admin-page.md#ii-adminhtml---add-a-hoot) (in part 11)
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

## I-C.

