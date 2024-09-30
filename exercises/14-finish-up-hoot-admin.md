# 14 - Finish up the hoot admin

## I. Create "View a single hoot" server GET endpoint 
- Endpoint in **api.js** is  `'/hoots/:id([0-9,a-z,A-Z,-]{36})'`
- Test it (either in the browser, or with Postman) with `http://localhost:3000/api/hoots/<valid-hoot-id>`

![screenshot](_images/express-23.png)

---

- Also test it with a non-existent id that is 36-characters long
  - http://localhost:3000/api/hoots/11111111-2222-3333-4444-555555555555
  - you'll get this response:

```json
{
  "error": "id: '11111111-2222-3333-4444-555555555555' not found"
}
```
- Test it with a bad `id` - http://localhost:3000/api/hoots/12345 - and you'll get the regular `404` page
---

## II. admin.html - Edit a hoot `<form>`

- Here's the code:

![screenshot](_images/express-XX.png)


---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**12 - `DELETE` at hoot**](12-delete-hoot-server-client.md)  |  [**IGME-430**](../) | TBA
