# Day 02 APIs, CRUD Operations, and First API Interaction

## What I studied today

Today I focused on:

- APIs (Application Programming Interfaces)
- CRUD operations
- interacting with APIs using HTTP methods
- basic web application concepts
- architecture and common security risks

The goal was to move from theory into actually interacting with a web API.

---

## API (Application Programming Interface)

An API is an **interface that allows different software systems to communicate with each other**.

In web applications, APIs usually:
- expose endpoints (URLs)
- accept HTTP requests
- return structured responses (often JSON)

They define:
- what actions are possible
- how requests must be formatted
- how data is returned

---

## CRUD operations

CRUD is a common model used when interacting with APIs.

| Operation | HTTP Method | Description |
|----------|------------|-------------|
| Create   | POST       | Add new data |
| Read     | GET        | Retrieve data |
| Update   | PUT        | Modify existing data |
| Delete   | DELETE     | Remove data |

Important note:
These operations usually act on **resources exposed by the API**, not directly on database rows (even though they often map to them internally).

---

## HTTP methods in practice

- **GET** → retrieve data  
- **POST** → send new data  
- **PUT** → update existing data  
- **DELETE** → remove data  

Each method changes how the server interprets the request.

---

## Web applications (quick overview)

Web applications:
- run in the browser
- use a **client-server model**
- consist of:
  - frontend (HTML, CSS, JavaScript)
  - backend (logic, database, APIs)

---

## Web application architecture (high-level)

Typical layers:

- **Presentation layer** → what the user sees
- **Application layer** → logic and processing
- **Data layer** → storage (databases)

Understanding this matters because:
- vulnerabilities can exist in any layer
- not all issues are coding mistakes (some are design flaws)

---

## Common web application risks

Some common vulnerability categories:

- SQL Injection  
- File Inclusion  
- Unrestricted File Upload  
- IDOR (Insecure Direct Object Reference)  
- Broken Access Control  

These often result from:
- poor validation
- bad access control
- unsafe assumptions about user input

---

## What I actually did
I interacted with a web API using `curl`.

### Reading data (GET)

I requested a resource from the API:

```bash
curl http://<TARGET>/api.php/city/london
````

Response (formatted with `jq`):

```json
[
  {
    "city_name": "London",
    "country_name": "(UK)"
  }
]
```

This showed me how data is returned as JSON.

---

### Formatting output with `jq`

```bash
curl http://<TARGET>/api.php/city/london | jq
```

This made the response easier to read and understand.

---

### Updating data (PUT)

I modified an existing resource:

```bash
curl -X PUT http://<TARGET>/api.php/city/london \
  -d '{"city_name":"New_City","country_name":"Test"}' \
  -H 'Content-Type: application/json'
```

Then verified the change:

```bash
curl http://<TARGET>/api.php/city/New_City | jq
```

This showed:

* how request bodies work
* why `Content-Type` matters
* how the server processes updates

---

### Creating and manipulating data

I also experimented with sending new values and modifying data manually.

This helped me understand:

* how APIs accept input
* how flexible endpoints can be
* how input directly affects stored data

---

### Deleting data

I used:

```bash
curl -X DELETE http://<TARGET>/api.php/city/<NAME>
```

This removed a resource from the API.

---

### Key takeaway from interaction

The most important realization:

> Changing the request (method, body, headers) directly changes server behavior.

This is where web security testing actually starts.

---

## What went well

* I moved from theory to actually interacting with an API
* CRUD operations made more sense after using them in practice
* Using `curl` + `jq` made responses easier to understand
* I could see cause and effect between request and response

---

## What was confusing
* nothing much confusing more the fact that the thory block was big today
 

---

## What I need to improve

* more hands-on experimentation instead of just reading
* staying focused during longer sessions (attention drift was noticeable)
* read the environment more carefully
* not assume setup issues too quickly

---

## What I think I understand now

* APIs expose structured endpoints that can be manipulated via HTTP
* CRUD operations map to real actions on resources
* JSON is commonly used to send and receive data
* modifying requests directly affects server-side behavior
* tools like `curl` give full control over requests

---

## Plan for next session

* continue with the web applications module
* focus on frontend vs backend concepts
* spend time actively experimenting with requests (not just reading)
* test how changing headers and input affects responses

---

## Session info

* Duration: ~3 hours
* Energy: Low

Note: Next time I want to keep sessions shorter and more focused.

```
