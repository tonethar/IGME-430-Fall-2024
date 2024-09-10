# Practice Quiz #1

**1) Spot the client. Spot the server.**
- Which of the below are *Clients*?
- Which of the below are *Servers*?
  
  a. banjo.rit.edu


  b. Chrome


  c. `curl` - ex. `curl http://localhost:3000/quotes`


  d. `curl` - ex.

```
curl --request POST --data '{
    "author": "TJ",
    "content": "No good deed goes unpunished.",
    "tags": [
        "uncategorized"
    ]
}' --header 'Content-Type: application/json' --location http://localhost:3000/quotes/
```

  e. `fetch()`


  f. A mapping app on mobile phone (ex. Google Maps)


  g. PHP on banjo


  h. Postman


  i. **quotes-app**


  j. **quotes-server**


  k. `XMLHttpRequest()` (aka `XHR`)


---
---


**2) Matching - associate the HTTP methods listed below with one of the 7 descriptions (choose 1 description per resource):**

    A. Creates a new resource
   
    B. Deletes the specified resource
   
    C. Partially modifies the specified resource
   
    D. Replaces the specified resource
   
    E. Returns the resource
   
    F. Returns the resource's HTTP headers (solely)
   
    G. Returns the HTTP header options (solely) for the target resource

```

   DELETE - 


   GET - 


   PATCH - 


   POST -


   PUT -

```

- Bonus: There are two missing methods (that we didn't talk about in class) - write them below and indicate their applicable desciption

```

   ???- 


   ???- 
```

---
---


**3) Label the *HTTP headers* below as a (choose 1):**

  A) *request* header
  
  B) *response* header
  
  C) *request* header AND a *response* header

```
Accept:


Accept-Language:


Accept-Encoding:


Access-Control-Allow-Origin:


Connection:


Content-Encoding:


Content-Type:


Date:


Host:


Keep-Alve:


Last-Modified:


Server:


User-Agent:
```

---
---

**4) HTTP Status Codes**
- We haven't seen many of these yet, but ...
- ... which HTTP status code did json-server return for each of the following queries (assume they are all *successful*):
  - `DELETE /quotes/guid`
  - `GET /quotes`
  - `GET /quotes/?id=5`
  - `PUT /quotes/guid`
  - `POST /quotes/`
  - `PATCH /quotes/guid`
- ... and how about for these *unsuccessful* queries
  - `GET /quotes/?id=666`
  - `DELETE /quotes/666`
 

---
---

**5) Reconstruct below from the following "fragments":**

```
POST /service.php HTTP/1.1
Host: www.rit.edu
Content-Type: application/json
Content-Length: 30
\n
{"name":"Timmy", "score":1000}
```

```
GET /service.php HTTP/1.1
Host: www.rit.edu
\n
```

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

### 5A. Request Phase
- `GET` service.php

```




```

- `POST` service.php

```



```

### 5B. Response Phase
- server.php

```




```









