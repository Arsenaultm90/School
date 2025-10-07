**HTTP (Hypertext Transfer Protocol)** is the fundamental protocol for transferring hypermedia documents, such as HTML, over the web. It operates on a **client-server model**, where:
- **Clients** (typically web browsers) initiate requests.
- **Servers** respond with resources like HTML, CSS, JavaScript, images, or data.

HTTP is **stateless**, meaning each request is independent, with no memory of previous interactions. However, mechanisms like cookies and sessions can introduce statefulness when needed.


---
#### Web Apps

In the context of web applications, HTTP facilitates:
- **Fetching Resources**: Retrieving HTML, CSS, JavaScript, images, and other assets.
- **Submitting Data**: Sending user inputs via forms or APIs.
- **Interactivity**: Using JavaScript to make asynchronous requests (AJAX) for dynamic content updates.
- **APIs**: Communicating with backend services using RESTful or GraphQL APIs.

This interaction allows web pages to be constructed from multiple resources, such as text content, layout instructions, images, videos, scripts, and more.


**HTTP Web App Cycle:**
1. **Request Initiation**: A user interacts with a web page (e.g., clicking a link or submitting a form).
2. **Client Sends Request**: The browser sends an HTTP request to the server.
3. **Server Processes Request**: The server handles the request, possibly interacting with databases or other services.
4. **Response Sent**: The server sends an HTTP response back to the client, which includes the requested resource or data.
5. **Rendering**: The browser processes the response and updates the user interface accordingly.

This cycle enables the dynamic and interactive nature of modern web applications.


**HTTP Methods:**
**GET**
- **Purpose**: Retrieve data from a server
- **Body**: ❌ No body (technically possible but not recommended/standard)
- **Headers**: ✅ Yes (common headers: Accept, Authorization, Cache-Control)
- **Query Parameters**: ✅ Yes (data goes in URL: `/api/users?id=123`)
- **Idempotent**: Yes (same request = same result)
- **Cacheable**: Yes

**POST**
- **Purpose**: Submit data to create a resource
- **Body**: ✅ Yes (JSON, form data, etc.)
- **Headers**: ✅ Yes (Content-Type, Authorization, etc.)
- **Query Parameters**: Optional (but data typically in body)
- **Idempotent**: No (multiple requests may create multiple resources)
- **Cacheable**: Usually no

**PUT**
- **Purpose**: Update/replace an entire resource
- **Body**: ✅ Yes (full resource representation)
- **Headers**: ✅ Yes
- **Query Parameters**: Optional
- **Idempotent**: Yes (same request = same result)
- **Cacheable**: No

**PATCH**
- **Purpose**: Partially update a resource
- **Body**: ✅ Yes (only fields to update)
- **Headers**: ✅ Yes
- **Query Parameters**: Optional
- **Idempotent**: Typically yes
- **Cacheable**: No

**DELETE**
- **Purpose**: Remove a resource
- **Body**: ❌ Usually no (but technically allowed)
- **Headers**: ✅ Yes (Authorization often required)
- **Query Parameters**: Optional (resource ID often in URL)
- **Idempotent**: Yes
- **Cacheable**: No

**HEAD**
- **Purpose**: Same as GET but without response body (metadata only)
- **Body**: ❌ No
- **Headers**: ✅ Yes
- **Query Parameters**: ✅ Yes
- **Idempotent**: Yes
- **Cacheable**: Yes

**OPTIONS**
- **Purpose**: Describe communication options for the target resource
- **Body**: ❌ Usually no
- **Headers**: ✅ Yes
- **Query Parameters**: Rare
- **Idempotent**: Yes
- **Cacheable**: No

These methods allow web applications to perform CRUD (Create, Read, Update, Delete) operations.


Modern web applications often utilize HTTP in conjunction with technologies like:
- **AJAX**: Enables asynchronous requests to update parts of a web page without reloading.
- **RESTful APIs**: Provide a standardized way for clients to interact with server resources.
- **Progressive Web Apps (PWAs)**: Use service workers to cache resources, allowing offline functionality and improved performance.

These technologies enhance user experience by enabling faster, more responsive, and offline-capable web applications.


---
#### HTTP Status Codes

![[Pasted image 20250925153835.png]]

