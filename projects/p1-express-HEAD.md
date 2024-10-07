# Express and sending headers (only)

## HEAD method
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/HEAD
  - *"The `HEAD` HTTP method requests the metadata of a resource in the form of headers that the server would have sent if the `GET` method was used instead."*
  - *"This method can be used in cases where a URL might produce a large download, for example, a `HEAD` request can read the `Content-Length` header to check the file size before downloading the file with a `GET.`"*

## express and `app.head()` (or `router.head()`)
- https://expressjs.com/en/5x/api.html#app.METHOD
  - *"The app.get() function is automatically called for the HTTP HEAD method in addition to the GET method if app.head() was not called for the path before app.get()."*
- 
