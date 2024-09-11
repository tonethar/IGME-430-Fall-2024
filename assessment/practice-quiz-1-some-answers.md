# Practice Quiz #1 - some answers

## \#5

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
