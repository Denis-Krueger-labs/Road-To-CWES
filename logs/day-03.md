---
layout: log
title: "Day 03 - Frontend vs Backend, Web Basics, and First Client-Side Attacks"
date: 2026-03-21
topics: ["Frontend", "Backend", "HTML", "CSS", "JavaScript", "XSS", "CSRF", "URL Encoding"]
summary: "How web applications are structured, how client-side attacks work, and first hands-on XSS payload testing."
status: complete
---

## What I studied today

Today I focused on:

- Frontend vs Backend
- basic web technologies (HTML, CSS, JavaScript)
- URL encoding
- client-side vulnerabilities
- XSS, HTML Injection, and CSRF basics

---

## Frontend vs Backend

### Frontend

Everything the user sees in the browser — HTML, CSS, JavaScript.

- **HTML** → structure of the page
- **CSS** → styling and layout
- **JavaScript** → functionality and interaction

### Backend

Handles all core logic and runs on the server.

| Component | Description |
|----------|------------|
| Backend Server | The system hosting the application |
| Web Server | Handles HTTP requests (e.g. Apache, Nginx, IIS) |
| Database | Stores application data |
| Framework | Used to build application logic |

The backend:
- processes requests
- handles authentication and authorization
- interacts with the database
- exposes APIs used by the frontend

### Security perspective

> Security issues can exist in both frontend and backend, and sometimes come from bad design, not just bad code.

---

## URL encoding

URL encoding (percent encoding) allows special characters to be safely transmitted in URLs.

| Character | Encoding |
|----------|---------|
| space | `%20` |
| `#` | `%23` |
| `&` | `%26` |

This matters because attackers may use encoding to bypass filters.

---

## Sensitive Data Exposure

Sensitive data exposure happens when information is visible to the user that should not be — credentials in source code, hidden API endpoints, comments left by developers.

> Always check the page source.

---

## HTML Injection

HTML Injection occurs when user input is inserted into a page without proper filtering, allowing modification of page content or injection of malicious HTML.

---

## Cross-Site Scripting (XSS)

XSS occurs when an attacker injects JavaScript into a page.

| Type | Description |
|---|---|
| Reflected | Input is returned immediately in the response |
| Stored | Input is stored and shown later |
| DOM-based | Happens entirely in the browser |

XSS can steal cookies, execute actions as the user, and manipulate page behavior.

---

## Cross-Site Request Forgery (CSRF)

CSRF tricks a user into performing actions they did not intend. It does not require JavaScript injection — it abuses trust between the browser and the application.

**XSS vs CSRF:**
- **XSS** → injects JavaScript into the page
- **CSRF** → tricks a user into performing actions

---

## What I actually did

### Built a simple frontend

```html
<h1 id="welcome">HTML CSS JS</h1>
```

```css
h1 { font-family: Impact, sans-serif; }
```

```js
document.getElementById('welcome').innerText += " Editors";
```

### Explored page source

Found in source code:

```html
<!-- TODO: remove test credentials admin:*** -->
```

This showed how comments in source code can expose sensitive data.

### Tested basic XSS payload

```html
"><img src=/ onerror=alert(document.cookie)>
```

This helped me understand how input is interpreted by the browser and how JavaScript can be executed through injected HTML.

### Also worked on an HTB machine

Obtained foothold relatively quickly; root took much longer and required more enumeration. Good reminder that "easy" ratings don't mean the full path is obvious — persistence and enumeration matter just as much as knowing individual concepts.

---

## What went well

- Understanding the difference between frontend and backend
- Actually interacting with frontend code
- Identifying sensitive data in source code
- Testing a real XSS payload

## What was confusing

- The difference between XSS and CSRF at first (clarified above)

## What I need to improve

- Read instructions more carefully
- Spend more time experimenting instead of rushing
- Strengthen understanding of XSS vs CSRF in practice

## Plan for next session

- Backend components: servers, databases, frameworks, APIs
- Backend vulnerabilities
- Continue practical testing

## Session info

- Duration: ~2.5 hours
- Energy: Medium
