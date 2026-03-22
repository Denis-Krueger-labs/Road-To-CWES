# Day 03 Frontend vs Backend, Web Basics, and First Client-Side Attacks

## What I studied today

Today I focused on:

- Frontend vs Backend
- basic web technologies (HTML, CSS, JavaScript)
- URL encoding
- client-side vulnerabilities
- XSS, HTML Injection, and CSRF basics

The goal was to understand how web applications are structured and how client-side issues can be exploited.

---

## Frontend vs Backend

### Frontend

The frontend is everything the user sees and interacts with in the browser.

It typically includes:
- **HTML** → structure of the page  
- **CSS** → styling and layout  
- **JavaScript** → functionality and interaction  

The browser interprets these components in real time.

Frontend responsibilities include:
- UI (User Interface)
- UX (User Experience)
- visual layout and interaction

---

### Backend

The backend handles all core logic and functionality.

It runs on the server and is usually not directly visible to the user.

Main backend components:

| Component | Description |
|----------|------------|
| Backend Server | The system hosting the application |
| Web Server | Handles HTTP requests (e.g. Apache, Nginx, IIS) |
| Database | Stores application data |
| Framework | Used to build application logic (e.g. Django, Laravel, Express) |

The backend:
- processes requests
- handles authentication and authorization
- interacts with the database
- exposes APIs used by the frontend

---

## Security perspective

A key takeaway:

> Security issues can exist in both frontend and backend, and sometimes come from bad design, not just bad code.

Important examples:
- trusting client-side data
- weak validation
- exposing sensitive data
- poor access control

---

## HTML basics

HTML forms the structure of a web page.

- elements are defined with tags (e.g. `<p>`, `<h1>`)
- elements are nested in a tree structure
- the browser parses and renders this structure

---

## URL encoding

URL encoding (percent encoding) allows special characters to be safely transmitted in URLs.

Examples:

| Character | Encoding |
|----------|---------|
| space | `%20` |
| `#` | `%23` |
| `&` | `%26` |

This matters because:
- input is often encoded before being processed
- attackers may use encoding to bypass filters

---

## CSS (Cascading Style Sheets)

CSS is used to style HTML elements.

Basic syntax:

```css
element {
  property: value;
}
````

It controls:

- layout
    
- colors
    
- fonts
    
- animations
    

---

## JavaScript

JavaScript is used to add logic and interactivity to web pages.

It runs in the browser and can:

- modify HTML dynamically
    
- send requests to the backend
    
- handle user input
    

---

## Sensitive Data Exposure

Sensitive data exposure happens when information is visible to the user that should not be.

Examples:

- credentials in source code
    
- hidden API endpoints
    
- comments left by developers
    

### Important takeaway

> Always check the page source.

---

## HTML Injection

HTML Injection occurs when user input is inserted into a page without proper filtering.

This can allow:

- modifying page content
    
- defacing pages
    
- injecting malicious HTML
    

---

## Cross-Site Scripting (XSS)

XSS occurs when an attacker injects JavaScript into a page.

Types of XSS:

|Type|Description|
|---|---|
|Reflected|Input is returned immediately in the response|
|Stored|Input is stored and shown later|
|DOM-based|Happens entirely in the browser|

XSS can:

- steal cookies
    
- execute actions as the user
    
- manipulate page behavior
    

---

## Cross-Site Request Forgery (CSRF)

CSRF tricks a user into performing actions they did not intend.

Example:

- a logged-in user unknowingly triggers a request that changes their password
    

Important:

- CSRF does not require JavaScript injection
    
- it abuses trust between the browser and the application
    

---

## What I actually did

This was the most important part of the session.

### Built a simple frontend

I created a basic HTML page and experimented with:

- HTML structure
    
- CSS styling
    
- JavaScript interaction
    

Example:

```html
<h1 id="welcome">HTML CSS JS</h1>
```

```css
h1 {
  font-family: Impact, sans-serif;
}
```

```js
document.getElementById('welcome').innerText += " Editors";
```

This helped me understand how frontend components work together.

---

### Additional practical work

Outside the main study topic, I also spent time working on an HTB machine.

- obtained foothold relatively quickly
- root took much longer and required a lot more enumeration and problem-solving
- this reminded me that “easy” machine ratings do not always mean the full path is obvious
- the machine was a good reminder that persistence, enumeration, and reviewing dead ends matter just as much as knowing individual concepts

I may document the full machine separately, but it was still an important part of today’s practical learning.

---

### Explored page source

While inspecting the source code, I found:

```html
<!-- TODO: remove test credentials admin:*** -->
```

This showed how:

- developers can accidentally expose sensitive data
    
- comments in source code can be valuable for attackers
    

---

### Tested basic XSS payload

I tried a simple payload:

```html
"><img src=/ onerror=alert(document.cookie)>
```

This helped me understand:

- how input is interpreted by the browser
    
- how JavaScript can be executed through injected HTML
    
- how cookies can potentially be accessed
    

---

## What went well

- understanding the difference between frontend and backend
    
- actually interacting with frontend code
    
- identifying sensitive data in source code
    
- testing a real XSS payload
    

---

## What was confusing

- the difference between XSS and CSRF at first
    

### Clarified understanding

- **XSS** → injects JavaScript into the page
    
- **CSRF** → tricks a user into performing actions
    

---

## Mistakes / friction

- misunderstanding how answers needed to be formatted in the lab
    
- small confusion due to wording of questions
    

---

## What I think I understand now

- frontend handles presentation, backend handles logic
    
- user input can be dangerous if not validated
    
- page source can reveal sensitive information
    
- XSS allows code execution in the browser
    
- CSRF abuses user trust and authentication
    

---

## What I need to improve

- read instructions more carefully
    
- spend more time experimenting instead of rushing
    
- strengthen understanding of XSS vs CSRF in practice
    

---

## Plan for next session

- backend components:
    
    - servers
        
    - databases
        
    - frameworks
        
    - APIs
        
- backend vulnerabilities
    
- continue practical testing and interaction
    

---

## Session info

- Duration: ~2.5 hours
    
- Energy: Medium
    
