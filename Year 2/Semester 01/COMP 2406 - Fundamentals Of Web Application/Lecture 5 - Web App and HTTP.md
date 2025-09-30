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
- **GET**: Retrieve data from the server (e.g., loading a webpage).
- **POST**: Submit data to the server (e.g., submitting a form).
- **PUT**: Update existing data on the server.
- **DELETE**: Remove data from the server.
- **PATCH**: Apply partial modifications to data.

These methods allow web applications to perform CRUD (Create, Read, Update, Delete) operations.


Modern web applications often utilize HTTP in conjunction with technologies like:
- **AJAX**: Enables asynchronous requests to update parts of a web page without reloading.
- **RESTful APIs**: Provide a standardized way for clients to interact with server resources.
- **Progressive Web Apps (PWAs)**: Use service workers to cache resources, allowing offline functionality and improved performance.

These technologies enhance user experience by enabling faster, more responsive, and offline-capable web applications.


---
#### HTTP Status Codes

![[Pasted image 20250925153835.png]]

