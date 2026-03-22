---
layout: log
title: "Day 01 — HTTP, HTTPS, cURL, Requests, Responses, and Headers"
date: 2026-03-20
topics: ["HTTP", "HTTPS", "cURL", "URL Structure", "HTTP Headers", "Status Codes"]
summary: "Core web basics — how HTTP/HTTPS work, URL anatomy, request/response structure, and hands-on cURL usage."
status: complete
---

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
```

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

1. The user enters a URL in the browser
2. The browser checks whether it can resolve the hostname locally (for example via `/etc/hosts`)
3. If not, it asks a DNS server to resolve the hostname to an IP address
4. The browser sends an HTTP request to the target server
5. The server responds with an HTTP response
6. The browser may then request additional resources like CSS, JavaScript, or images

---

## cURL

**cURL** is a command-line tool used to send requests to URLs. It supports HTTP, HTTPS, FTP, SFTP, and more. Useful because it lets you interact with web servers directly without using a browser.

---

## HTTPS

**HTTPS** is the secure version of HTTP. Traffic is protected using TLS encryption. Default port is **443**.

HTTPS protects the contents of the communication, but not everything is hidden — the destination IP is still visible, and DNS lookups may still reveal the target hostname.

---

## HTTP requests and responses

### Request line

```text
GET /users/login.html HTTP/1.1
```

| Field   | Example             | Description                  |
| ------- | ------------------- | ---------------------------- |
| Method  | `GET`               | The action to perform        |
| Path    | `/users/login.html` | The resource being requested |
| Version | `HTTP/1.1`          | The HTTP version being used  |

### Response line

```text
HTTP/1.1 200 OK
```

---

## HTTP headers

### General headers

| Header     | Example                               | Description                                          |
| ---------- | ------------------------------------- | ---------------------------------------------------- |
| Date       | `Date: Wed, 16 Feb 2022 10:38:44 GMT` | The time the message was created                     |
| Connection | `Connection: close`                   | Whether the connection should stay open or be closed |

### Request headers

| Header        | Example                                  | Description                                            |
| ------------- | ---------------------------------------- | ------------------------------------------------------ |
| Host          | `Host: www.inlanefreight.com`            | Specifies which host is being requested                |
| User-Agent    | `User-Agent: curl/7.77.0`                | Identifies the client making the request               |
| Authorization | `Authorization: Basic ...`               | Sends authentication information                       |
| Cookie        | `Cookie: PHPSESSID=b4e4fbd93540`         | Sends stored cookie values to the server               |

### Response headers

| Header           | Example                                     | Description                                              |
| ---------------- | ------------------------------------------- | -------------------------------------------------------- |
| Server           | `Server: Apache/2.2.14 (Win32)`             | Provides information about the web server                |
| Set-Cookie       | `Set-Cookie: PHPSESSID=b4e4fbd93540`        | Tells the client to store a cookie                       |

### Security headers

| Header                    | Example                                       | Description                                    |
| ------------------------- | --------------------------------------------- | ---------------------------------------------- |
| Content-Security-Policy   | `Content-Security-Policy: script-src 'self'`  | Restricts which resources the browser may load |
| Strict-Transport-Security | `Strict-Transport-Security: max-age=31536000` | Forces the browser to use HTTPS                |

---

## HTTP methods

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

| Class | Meaning       |
| ----- | ------------- |
| 1xx   | Informational |
| 2xx   | Success       |
| 3xx   | Redirection   |
| 4xx   | Client error  |
| 5xx   | Server error  |

---

## GET vs POST

**GET** — used to request resources, parameters in the URL, easy to observe.

**POST** — used to send data to the server in the request body. POST is **not automatically private** — its security depends on whether HTTPS is used.

---

## What went well

* The material was mostly easy to understand
* cURL usage made things feel more concrete
* I started connecting browser behavior with lower-level request behavior

## What needs improvement

* Get more comfortable with practical cURL usage — `-X`, `-H`, and other flags
* Move from "I understand the theory" to "I can control and test requests myself"

## Friction / confusion

At one point I got frustrated because I thought I needed to be inside a VM to continue. Later I realized the target IP was public and I did not need the VPN for that step. Useful reminder: read the environment before assuming the setup is wrong.

## Plan for next session

* Finish the CRUD API part of the web requests module
* Spend more time experimenting with cURL instead of only reading about it
