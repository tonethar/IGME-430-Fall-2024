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

---

## III. json-server
- https://www.npmjs.com/package/json-server

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
