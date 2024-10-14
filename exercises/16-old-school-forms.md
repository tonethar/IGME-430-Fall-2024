# 16 - "Old School" `<form>`s

- So far this semester, we have been using HTML forms in conjunction with client-side JavaScript to send data to our node server.
- But HTML forms have been around since the very beginning of the web, and can function in the web browser without utilizing *client-side* scripting
- Reference:
  - https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form
  - https://www.w3schools.com/html/html_forms.asp

---

## I. A simple GET request

- Add the following to **admin.html**

```html
<hr>

<h2>VII. View one quote (Old School GET, no JS)!</h2>
<form action="/quotes" method="GET">
  <label>Id: <input type="text" name="id" size="36"></label><br><br>
  <button type="submit">Send "No JS" Request to <kbd>/quotes?id=</kbd></button>
</form>

<p><i>This will re-direct the browser to the <kbd>/quotes?id=</kbd> endpoint, and display whatever the server sent back.</i></p>
<p>You can use <kbd>4c6217c3-c6e5-460b-8f8f-0df64ad6fef2</kbd> to view the mark Twain quote.</p>

```

- Note the `action` of the form, which is the URL it is going to call when the submit button is clicked
- Note the form `method` of `GET`, which means that the form will utlize the *query string* to send data to the node server
- PS - we are calling the `/quotes?id=xxx` endpoint here rather than `/api/hoot/xxx` because we don't already have query string handling with our `/api/hoot/xxx` endpoint

---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**15 -  Notes & Errata**](15-notes-and-errata.md)  |  [**IGME-430**](../) | TBA
