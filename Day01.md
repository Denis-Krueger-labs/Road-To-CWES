# Day 01 – HTTP, HTTPS, cURL, Requests, Responses, and Headers

## What I studied today

Today I worked through core web basics:

- HTTP
- HTTPS
- URL structure
- cURL
- HTTP requests and responses
- HTTP headers
- request methods
- status codes
- GET vs POST

The goal was to strengthen my understanding of how web communication actually works before going deeper into web exploitation.

---

## HTTP

**HTTP (Hypertext Transfer Protocol)** is used for communication between a client and a server.

- the **client** sends a request
- the **server** sends a response
- the default port for HTTP is **80**

HTTP is the protocol used to request and transfer web resources such as HTML pages, images, scripts, and more.

---

## URL structure

Websites are accessed through a **URL (Uniform Resource Locator)**.

Example:

```text
http://admin:password@inlanefreight.com:80/dashboard.php?login=true#status
````

### URL components

| Component    | Example                 | Description                                      |
| ------------ | ----------------------- | ------------------------------------------------ |
| Scheme       | `http://` or `https://` | Identifies the protocol being used               |
| User Info    | `admin:password@`       | Optional credentials used for authentication     |
| Host         | `inlanefreight.com`     | The hostname or IP address of the target         |
| Port         | `:80`                   | The network port used for the connection         |
| Path         | `/dashboard.php`        | The resource being requested                     |
| Query String | `?login=true`           | Parameters passed to the application             |
| Fragment     | `#status`               | A client-side reference to a section of the page |

### Notes

* If no port is specified, **HTTP defaults to 80** and **HTTPS defaults to 443**
* Fragments (`#something`) are processed by the browser and are generally **not sent to the server**

---

## Basic HTTP flow

A simplified HTTP flow looks like this:

1. The user enters a URL in the browser
2. The browser checks whether it can resolve the hostname locally (for example via `/etc/hosts`)
3. If not, it asks a DNS server to resolve the hostname to an IP address
4. The browser sends an HTTP request to the target server
5. The server responds with an HTTP response
6. The browser may then request additional resources like CSS, JavaScript, or images

### Important note

In real web traffic, this is often messier than a single request/response:

* there may be redirects
* many resources may be requested
* cookies and headers influence behavior
* sessions may change what the user sees

---

## cURL

**cURL** is a command-line tool used to send requests to URLs.

It supports many protocols, including:

* HTTP
* HTTPS
* FTP
* SFTP

cURL is useful because it lets you interact with web servers directly without using a browser.

### cURL and libcurl

* **cURL** is the command-line tool
* **libcurl** is the library underneath it

A simple way to think about it:

* cURL = the dashboard / controls
* libcurl = the engine doing the work

---

## HTTPS

**HTTPS (Hypertext Transfer Protocol Secure)** is the secure version of HTTP.

* HTTP traffic is sent in plaintext
* HTTPS protects traffic using TLS encryption
* the default port for HTTPS is **443**

### Important note

HTTPS protects the contents of the communication, but not everything is hidden. For example:

* the destination IP is still visible
* DNS lookups may still reveal the target hostname unless additional protections are used
* some metadata can still be observed

---

## Basic HTTPS flow

A simplified HTTPS flow looks like this:

1. The user enters a URL
2. The browser connects to the server
3. If needed, the server redirects HTTP traffic to HTTPS
4. The browser and server perform a TLS handshake
5. Certificates are used to verify the server
6. Session keys are established
7. Encrypted communication begins

---

## cURL with HTTPS

When using cURL against HTTPS targets, certificate validation matters.

If the certificate is self-signed or otherwise not trusted, cURL may reject the connection.

The `-k` option tells cURL to ignore certificate validation errors.

### Important note

This is useful in labs, test environments, or CTFs, but it should be used carefully because it disables certificate verification.

---

## HTTP requests and responses

### HTTP request line

Example:

```text
GET /users/login.html HTTP/1.1
```

This contains three main parts:

| Field   | Example             | Description                  |
| ------- | ------------------- | ---------------------------- |
| Method  | `GET`               | The action to perform        |
| Path    | `/users/login.html` | The resource being requested |
| Version | `HTTP/1.1`          | The HTTP version being used  |

---

### HTTP response line

Example:

```text
HTTP/1.1 200 OK
```

This contains:

* the HTTP version
* the response status code
* the response status text

---

## HTTP headers

Headers provide extra information about requests and responses.

They can describe:

* the message itself
* the content being transferred
* the client
* the server
* security rules

---

## General headers

General headers can appear in both requests and responses.

| Header     | Example                               | Description                                          |
| ---------- | ------------------------------------- | ---------------------------------------------------- |
| Date       | `Date: Wed, 16 Feb 2022 10:38:44 GMT` | The time the message was created                     |
| Connection | `Connection: close`                   | Whether the connection should stay open or be closed |

---

## Entity / content-related headers

These describe the data being transferred.

| Header                     | Example                             | Description                                                                     |
| -------------------------- | ----------------------------------- | ------------------------------------------------------------------------------- |
| Content-Type               | `Content-Type: text/html`           | Describes the type of content being transferred                                 |
| Content-Length             | `Content-Length: 385`               | Size of the message body                                                        |
| Content-Encoding           | `Content-Encoding: gzip`            | Encoding or compression applied to the content                                  |
| Content-Type with boundary | `multipart/form-data; boundary=...` | Used when multiple parts are included in a single request, such as file uploads |

### Note

I wrote down `Media-Type` separately during study, but in practice this is usually represented through `Content-Type`.

---

## Request headers

These appear in requests sent by the client.

| Header        | Example                                  | Description                                            |
| ------------- | ---------------------------------------- | ------------------------------------------------------ |
| Host          | `Host: www.inlanefreight.com`            | Specifies which host is being requested                |
| User-Agent    | `User-Agent: curl/7.77.0`                | Identifies the client making the request               |
| Referer       | `Referer: http://www.inlanefreight.com/` | Shows where the request came from                      |
| Accept        | `Accept: */*`                            | Describes which response formats the client can accept |
| Cookie        | `Cookie: PHPSESSID=b4e4fbd93540`         | Sends stored cookie values to the server               |
| Authorization | `Authorization: Basic ...`               | Sends authentication information                       |

### Security note

Headers like `Referer`, `User-Agent`, and even some authentication-related values should never be trusted blindly by the server, because many can be modified by the client.

---

## Response headers

These appear in responses sent by the server.

| Header           | Example                                     | Description                                              |
| ---------------- | ------------------------------------------- | -------------------------------------------------------- |
| Server           | `Server: Apache/2.2.14 (Win32)`             | Provides information about the web server                |
| Set-Cookie       | `Set-Cookie: PHPSESSID=b4e4fbd93540`        | Tells the client to store a cookie                       |
| WWW-Authenticate | `WWW-Authenticate: Basic realm="localhost"` | Tells the client what type of authentication is required |

---

## Security headers

These are response headers that help define browser security behavior.

| Header                    | Example                                       | Description                                    |
| ------------------------- | --------------------------------------------- | ---------------------------------------------- |
| Content-Security-Policy   | `Content-Security-Policy: script-src 'self'`  | Restricts which resources the browser may load |
| Strict-Transport-Security | `Strict-Transport-Security: max-age=31536000` | Forces the browser to use HTTPS                |
| Referrer-Policy           | `Referrer-Policy: origin`                     | Controls how much referrer information is sent |

---

## HTTP methods

Common HTTP methods include:

| Method  | Description                                             |
| ------- | ------------------------------------------------------- |
| GET     | Requests a resource from the server                     |
| POST    | Sends data to the server, usually in the request body   |
| HEAD    | Requests only the headers that would be returned by GET |
| PUT     | Uploads or replaces a resource                          |
| DELETE  | Deletes a resource                                      |
| OPTIONS | Shows which methods are allowed                         |
| PATCH   | Applies partial changes to a resource                   |

---

## Status codes

HTTP status codes show the result of a request.

### Status code classes

| Class | Meaning       |
| ----- | ------------- |
| 1xx   | Informational |
| 2xx   | Success       |
| 3xx   | Redirection   |
| 4xx   | Client error  |
| 5xx   | Server error  |

### Common examples

| Code                      | Description                  |
| ------------------------- | ---------------------------- |
| 200 OK                    | Request succeeded            |
| 302 Found                 | Redirect to another location |
| 400 Bad Request           | Malformed request            |
| 403 Forbidden             | Access denied                |
| 404 Not Found             | Resource does not exist      |
| 500 Internal Server Error | Server-side problem          |

---

## GET vs POST

### GET

* used to request resources
* parameters are usually sent in the URL
* commonly used to retrieve pages or data
* easy to observe in browser devtools and in URLs

### POST

* used to send data to the server
* parameters are usually sent in the request body
* commonly used for forms, logins, uploads, and API actions

### Important note

POST is **not automatically private or secure** just because the data is not in the URL.
Its security depends on the surrounding context, especially whether HTTPS is used.

### Practical advantages of POST

* can send larger amounts of data
* does not place parameters directly in the URL
* supports request bodies for structured input

---

## What went well

* The material was mostly easy to understand
* Seeing how requests work through simple cURL usage made things feel more concrete
* Understanding the role of cURL and how it interacts with web requests was useful
* I started connecting browser behavior with lower-level request behavior

---

## What needs improvement

* I want to get more comfortable with practical cURL usage, especially flags like:

  * `-X`
  * `-H`
  * other options that let me modify requests directly
* I want to move from “I understand the theory” to “I can control and test requests myself”
* I also want to pay more attention to what actually changes when I manipulate requests manually

---

## Friction / confusion I noticed

At one point I got frustrated because I thought I needed to be inside a VM to continue.
Later I realized the target IP was public and I did not need the VPN setup for that step.

That was a useful reminder:

* not every web target lives inside a lab VPN
* I need to read the environment more carefully before assuming the setup is wrong

---

## Plan for tomorrow

* finish the CRUD API part of the web requests module
* continue along the path if I still have time
* spend some time experimenting more actively with cURL instead of only reading about it
* focus especially on manually changing request details and observing the response
---
