# Practice Quiz #1 - partial key

- Quiz is here: [practice-quiz-1.md](practice-quiz-1.md)

## Question \#1 - Spot the client. Spot the server.
- https://en.wikipedia.org/wiki/Client_(computing)
- https://en.wikipedia.org/wiki/Server_(computing)
- https://en.wikipedia.org/wiki/Client%E2%80%93server_model

## Question \#2 - HTTP Methods
- https://en.wikipedia.org/wiki/HTTP#Request_methods
- The 2 methods miossing from the list are `HEAD` and `OPTIONS` 

## Question \#3- HTTP Headers
- https://en.wikipedia.org/wiki/List_of_HTTP_header_fields

## Question \#4- HTTP Status Codes
- https://en.wikipedia.org/wiki/List_of_HTTP_status_codes

## Question \#5

- **`GET` request**
```
GET /service.php HTTP/1.1
Host: www.rit.edu
\n
```

- **`POST` request**
```
POST /service.php HTTP/1.1
Host: www.rit.edu
Content-Type: application/json
Content-Length: 30
\n
{"name":"Timmy", "score":1000}
```

- **`GET` response**
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Server: Apache
Content-Length: 3272
\n
<!DOCTYPE html>
<html>
<!-- ... HTML content ... -->
</html>
```
