**REST** stands for **Representational State Transfer**.  
It’s an **architectural style** for designing **networked applications**, most commonly used for building **web APIs**.

A **RESTful API** is one that conforms to the principles and constraints defined by REST.

**Resources**
The key **abstraction of information** in REST is a [resource](https://restfulapi.net/resource-naming/). Any information that we can name can be a resource. For example, a REST resource can be a document or image, a temporal service, a collection of other resources, or a non-virtual object (e.g., a person).

The state of the resource at any particular time is known as the **resource representation**. The resource representations consist of:
- the **data**
- the **metadata** describing the data
- and the **hypermedia links** that can help the clients transition to the next desired state.

**Representation**
- When a client requests that resource, the server sends back a **representation** — typically in JSON, XML, or HTML.  
    The resource itself (like the database row) stays on the server.
- The representation _represents_ the current **state** of that resource.
Example:
```
{
  "id": 1,
  "name": "Matt",
  "email": "matt@example.com"
}
```
This JSON _represents_ the state of user #1 at the moment of the request.

**State Transfer**
- The **state** being transferred is the **application state** between the **client and the server**, not the server’s own persistent state.
- Every time the client makes a request and receives a response, some part of the _application’s state_ changes:
    - The client might display a new page.
    - The user might move from viewing a list of books to viewing one book’s details.

So “Representational State Transfer” literally means:
> _Transferring representations of resources between client and server, changing the client’s application state in the process._


---
#### **Core Principles**

There are **six constraints** that define REST architecture.  
If an API adheres to these, it’s considered **RESTful**.

##### 1️. Client–Server Architecture
- **Separation of concerns**:  
    The client (frontend) handles the user interface; the server handles data and logic.
- Benefits:
    - Simpler client and server development
    - Components can evolve independently

##### 2️. Statelessness
- Each **request from client → server** must contain **all the information** the server needs to process it.
- The server **does not store client context** between requests.
- Benefits:
    - Scalability (easier to distribute across servers)
    - Simpler failure recovery
- Drawback:
    - Client must send authentication & session info with every request

##### 3️. Cacheability
- Responses from the server can be **explicitly marked as cacheable or non-cacheable**.
- Caching improves **performance** and **reduces server load**.
- Example:  
    `Cache-Control: max-age=3600` (1 hour caching)

##### 4️. Uniform Interface
- The most **important** REST constraint.
- Defines **standard ways** for clients and servers to communicate.
- Simplifies architecture and decouples client/server.

Key elements of the uniform interface:
- **Identification of resources** – The interface must uniquely identify each resource involved in the interaction between the client and the server.
- **Manipulation of resources through representations** – The resources should have uniform representations in the server response. API consumers should use these representations to modify the resource state in the server.
- **Self-descriptive messages** – Each resource representation should carry enough information to describe how to process the message. It should also provide information on the additional actions that the client can perform on the resource.
- **Hypermedia as the engine of application state** – The client should have only the initial URI of the application. The client application should dynamically drive all other resources and interactions with the use of hyperlinks.

##### 5️. Layered System
- REST allows **intermediate layers** (e.g., proxies, load balancers, caches) between client and server.
- Each layer only knows about the next one in line.

##### 6️. Code-on-Demand (Optional)
- Server can provide **executable code** (like JavaScript) to clients for flexibility.
- Often not used in APIs.


---
#### **HTTP Status Codes**

|Code|Meaning|Usage|
|---|---|---|
|**200 OK**|Success|Standard successful response|
|**201 Created**|Resource created|After `POST`|
|**204 No Content**|Success, no data|After `DELETE` or `PUT`|
|**400 Bad Request**|Invalid request|Missing fields, etc.|
|**401 Unauthorized**|Authentication required||
|**403 Forbidden**|Authenticated but not allowed||
|**404 Not Found**|Resource doesn’t exist||
|**409 Conflict**|Resource conflict (e.g., duplicate)||
|**500 Internal Server Error**|Server problem||
