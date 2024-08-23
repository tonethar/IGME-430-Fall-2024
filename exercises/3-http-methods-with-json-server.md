# 3 - Exploring HTTP methods with json-server

## I. Overview

## II. Overview of HTTP Messaging (Request & Response Phases)
- Source: https://www.rfc-editor.org/rfc/rfc9110#name-example-message-exchange

- The following example illustrates a typical HTTP/1.1 message exchange for a GET request (Section 9.3.1) on the URI `http://www.example.com/hello.txt`:

**Client *request:***

```
GET /hello.txt HTTP/1.1
User-Agent: curl/7.64.1
Host: www.example.com
Accept-Language: en, mi
```

**Server *response:***

```
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
ETag: "34aa387-d-1568eb00"
Accept-Ranges: bytes
Content-Length: 51
Vary: Accept-Encoding
Content-Type: text/plain

Hello World! My content includes a trailing CRLF.
```

---
# HTTP Request Phase
---

### A. HTTP Methods
- Safe methods
- Idempotent Methods
- https://www.rfc-editor.org/rfc/rfc9110#section-9.3

### B. HTTP Request Headers


---
# HTTP Response Phase
---

### A. HTTP Status Codes
- https://www.rfc-editor.org/rfc/rfc9110#name-status-codes

### B. HTTP Response Headers

### C. The content (text, images, etc)

---
___

## III. json-server
- https://www.npmjs.com/package/json-server

1. Create a new folder named **quotes-server**

2. Inside of the **quotes-server** folder, create a **data** folder

3. Put the **quotes-data.json** file into the **quotes-server/data/** folder

4. Open up Gitbash (or Terminal on Mac) and make sure that the **quotes-server** folder is the *current working directory*

5. To create a boilerplate **package.json** file type `npm init -y`

6. To install the `json-server` package type `npm i json-server`

7. To run the server type `npx json-server quotes-data.json`

8. That's it - to test the GET endpoints of the server:

    - In a browser, head to http://localhost:3000/0 to see the first quotes, http://localhost:3000/1 to see the second quote and so on
    - From the command line, `curl http://localhost:3000/0` works (if you have `curl` installed)
    - You can also use Postman to test the endpoints
    - We don't have the random quote functionality here, but your quotes app code can point at and download a specific quote - http://localhost:3000/4 is the last one - go ahead an try that now (don't forget to run the quotes app off of live server) 

10. 

---

## IV. Reference
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Resources_and_specifications
- HTTP Protocol Specifications:
  - HTTP/1.0 - https://www.w3.org/Protocols/HTTP/1.0/draft-ietf-http-v10-spec-01.html
  - HTTP/1.1 - https://www.ietf.org/rfc/rfc2616.txt
  - HTTP/1.1 (Current Spec) - https://www.rfc-editor.org/rfc/rfc9110


---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**2 - Ajax, Web Services, HTTP Headers (Accept & Content-type)**](2-ajax-web-services-accept-headers.md)  |  [**IGME-430**](../) | TBA
