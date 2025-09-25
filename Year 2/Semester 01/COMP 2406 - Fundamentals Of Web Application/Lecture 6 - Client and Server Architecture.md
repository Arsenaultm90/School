#### Client vs Server

**Client:**
- The **initiator** of communication.
- Requests resources or services from a server.
- Typically a web browser, mobile app, or any device requesting data.
- Example: You type `example.com` in your browser; your browser is the client.

**Server:**
- The **responder**.
- Stores, manages, and provides resources or services.
- Waits for client requests and sends back responses.
- Example: The web server hosting `example.com` HTML, CSS, and images.

**Key Difference:**
- **Client:** sends requests, consumes resources.
- **Server:** waits for requests, serves resources.


---
#### Resource Organization, Naming Schemes, and Protocols

**Resource Organization:**
- Servers store resources (files, data, APIs) in a structured way so they can be easily accessed.
- Example: `/images/logo.png` or `/api/users/123`.

**Naming Schemes (URLs):**
- Each resource has a unique identifier — typically a **URL (Uniform Resource Locator)**.
- URL structure: `protocol://domain:port/path?query#fragment`
    - `https://example.com:443/path/to/resource?search=query#section1`

**Protocols:**
- Define **rules for communication** between client and server.
- Most common: **HTTP/HTTPS** for web apps.
- Protocols ensure both client and server “speak the same language,” so requests and responses are understood.


---
#### Request/Response Cycle

The core of client-server interaction:
1. **Client sends a request:**
    - Example: Browser requests `GET /index.html` from server.
2. **Server receives request:**
    - Parses the request, locates the resource, may query a database or perform processing.
3. **Server sends a response:**
    - Includes **status code** (200 OK, 404 Not Found), headers, and body (HTML, JSON, etc.).
4. **Client processes response:**
    - Renders web page, updates UI, or performs other actions.

**Flowchart Example:**
```
[Client] --request--> [Server]
[Client] <--response-- [Server]
```
Each request is **independent** in HTTP (stateless), though sessions/cookies can maintain state.


---
#### Benefits of Asynchronous Processing

**Asynchronous operations** allow servers and clients to handle multiple tasks **without blocking**.

In web apps:
    - Client can continue interacting with the page while waiting for data.
    - Server can handle multiple requests simultaneously without waiting for one to finish.

**Example in a Web App:**
```
// Client-side AJAX request
fetch('/api/data')
  .then(response => response.json())
  .then(data => console.log(data));

// Browser remains responsive while waiting for the response
```

**Benefits:**
- **Better user experience:** Pages don’t freeze while waiting for requests.
- **Higher server efficiency:** Can handle multiple requests concurrently.
- **Responsive applications:** Useful for loading dynamic content without full page reloads.

