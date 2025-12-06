# HTML and CSS

#### **HTML**
HTML (HyperText Markup Language) defines the **structure and content** of a webpage.

##### HTML Document Structure
Every HTML document follows this structure:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Example</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
  <!-- Content goes here -->
</body>
</html>
```
- **<!DOCTYPE html>**  
    Tells the browser to use **HTML5**; ensures standards mode.
- **html**  
    Root of the document.
- **head**  
    Metadata, CSS links, scripts that shouldn’t appear in the page visually.
- **meta charset="UTF-8"**  
    Character encoding (important for exam questions).
- **meta name="viewport"**  
    Makes websites responsive on mobile.
- **body**  
    Visible content: text, images, links, forms, etc.


##### **HTML Elements and Structure**
**Block-level elements (take full width)**
- `<div>`
- `<p>`
- `<h1>` to `<h6>`
- `<section>`
- `<article>`
- `<header>`, `<footer>`
- `<ul>`, `<ol>`

**Inline elements (take only needed width)**
- `<span>`
- `<a>`
- `<strong>`, `<em>`
- `<img>`
- `<label>`

**Putting a block element inside an inline element is technically invalid.

##### **Semantic HTML**
Used for **accessibility**, **SEO**, and **structure**.
Common elements:
- `<header>`
- `<footer>`
- `<main>`
- `<nav>`
- `<section>`
- `<article>`
- `<aside>`
- `<figure>` + `<figcaption>`

##### Why semantic HTML matters:
- Screen readers understand your layout better
- Improves SEO (search engines understand importance of content)
- Replaces `<div>` soup


##### **Attributes**
Attributes add extra functionality:

**Common attributes:**
- `id` — unique identifier
- `class` — reusable style/JS hook
- `src` — image/script URL
- `href` — links
- `alt` — description for images (required for accessibility)
- `style` — inline CSS (bad practice except for quick demos)
- `data-*` — custom attributes used in JS (ex: `data-id="5"`)

**Boolean attributes:**
- `disabled`
- `checked`
- `required`
- `readonly`

Boolean attributes do not need values:
```
<input disabled>
```


##### **Forms and Input Fields**
Key elements:
```
<form action="/login" method="POST">
  <input type="text" name="email" required>
  <input type="password" name="pass">
  <button type="submit">Login</button>
</form>
```
- **method="GET"**  
    Sends form data in **URL query string**  
    _Visible & insecure for passwords._
- **method="POST"**  
    Sends data in the **request body**  
    _Used for login, updates, creation._
- **name="" attribute**  
    The server **only receives inputs that have a name attribute**.
- **label + for=""**  
    Improves accessibility.


##### **The DOM Relationship**
HTML is converted into the **DOM (Document Object Model)**:
- Tree of nodes
- Every tag becomes a node
- JavaScript manipulates DOM nodes



#### **CSS**

**External Stylesheet:**
```
<link rel="stylesheet" href="styles.css">
```

**Internal Stylesheet:**
```
<style>
  h1 { color: blue; }
</style>
```

**Inline Style:**
```
<h1 style="color: blue;">Hello</h1>
```


**Selectors**:
```
p       { }   /* element */
#title  { }   /* id (unique) */
.button { }   /* class */
```


**CSS Specificity:**
```
pecificity determines **which rules win** when multiple rules apply.

Order (highest → lowest):
1. Inline styles → `style=""`
2. IDs → `#id`
3. Classes → `.class`
4. Elements → `div`, `p`, `h1`
5. Universal → `*`
```


##### CSS Box Model
```
┌────────────────────────────┐
│          MARGIN            │ ← Space *outside* the element
│ ┌────────────────────────┐ │
│ │        BORDER          │ │ ← The visible boundary line
│ │   ┌──────────────────┐ │ │
│ │   │     PADDING      │ │ │ ← Space *inside* between content and border
│ │   │  ┌────────────┐  │ │ │
│ │   │  │  CONTENT   │  │ │ │ ← Text, images, etc.
│ │   │  └────────────┘  │ │ │
│ │   └──────────────────┘ │ │
│ └────────────────────────┘ │
└────────────────────────────┘

```

Properties:
- `margin`
	- Margin is the **space OUTSIDE the element**, separating it from neighboring elements.
	- Pushes the element away from others.
	- Does **not** affect the element’s size.
	- Background colour **does not extend into margin**.
	- Vertical margins collapse, Horizontal margins do not
- `border`
	- A border is the **line that surrounds the padding and content**.
	- Visible outline around the element.
	- Has **thickness**, **style**, and **colour**.
	- Adds to the element’s total size
- `padding`
	- Padding is the **space INSIDE the element**, between the **content** and the **border**.
	- Expands the **inside** of the box.
	- Increases the element's visible size **without pushing away neighbouring elements**.
	- Background colour **extends into the padding area**.
- `width` / `height`

**Default sizing uses content-box** (width = content only)
To include padding/border inside width:
```
* { box-sizing: border-box; }
```









---
# JavaScript

JavaScript is a **dynamic**, **interpreted**, **prototype-based**, **single-threaded**, **event-driven** programming language used for web development.

#### **JS Variable Types & Declarations**

 `var`
- Function-scoped
- Hoisted (initialized as `undefined`)
- Allows redeclaration
- Avoid using it in modern code

`let`
- Block-scoped
- Hoisted but **not initialized** → Temporal Dead Zone
- Cannot be redeclared in same scope

`const`
- Block-scoped
- Must be initialized
- Value cannot be reassigned, _but object properties CAN be changed_


##### TypeOf - Always returns type string
```
typeof 5          // "number"
typeof "hello"    // "string"
typeof true       // "boolean"
typeof {}         // "object"
typeof undefined  // "undefined"
typeof []         // "object"
typeof null       // "object"
typeof NaN        // "number"
```


#### Arrays
```
const arr = [1, 2, 3];
arr.push(4);   // adds
arr.pop();     // removes
arr.length;    // size
```
- `map`
- `filter`
- `reduce`
- `forEach`
- `includes`
- `find`


#### Functions
**Function Declaration :**
```
function add(a, b) { return a + b; }
```

**Function Expression :**
```
const add = function(a, b) { return a + b; }
```

**Arrow Function :**
```
const add = (a, b) => a + b;
```



#### **Hoisting**
**Hoisting** is JavaScript’s behaviour of moving **declarations** to the top of their scope _during compilation_, before the code runs.

- Function declarations: **hoisted fully**
- var: **hoisted but initialized to undefined**
- let/const: **hoisted but not initialized** (TDZ)

**Example :**
```
Function Declerations
sayHi();   // works!

function sayHi() {
  console.log("Hello");
}


var - Hoisted, but initialized to undefined
console.log(a); // undefined
var a = 5;


let and const - Hoisted, but not initialized (Temporal Dead Zone)
console.log(b); // ReferenceError
let b = 5;
```



#### **Truthy and Falsy Values**
**Falsy Values :**
- `false`
- `0`
- `""` (empty string)
- `null`
- `undefined`
- `NaN`

**Everything else is truthy :**
- `"0"`
- `"false"`
- `[]`
- `{}`



#### **The DOM and Events (JS + browser)**
```
const btn = document.getElementById("btn");
btn.addEventListener("click", () => {
  console.log("clicked");
});
```
- DOM is a **tree of nodes**
- `querySelector` accepts CSS selectors
- Events bubble from child → parent (event bubbling)


#### **Asynchronous JavaScript**
**JavaScript uses :**
- Event loop
- Callback queue
- Microtask queue (promises)
- Web APIs (timers, fetch)



#### Promises
```
const p = new Promise((resolve, reject) => {
  resolve("success");
});
```

**then/catch :**
```
p.then(val => console.log(val))
 .catch(err => console.error(err));
```

**async/await :**
```
async function load() {
  const result = await fetch("/data");
}
```

**Promise states:**
1. pending
2. fulfilled
3. rejected



#### JSON
```
const obj = JSON.parse('{"name":"Matt"}');
const str = JSON.stringify(obj);
```
`JSON` is **text format**, not JS objects.



#### Error Handling
```
try {
  throw new Error("bad");
} catch (err) {
  console.log(err.message);
}
```
- `ReferenceError`
- `TypeError`
- `SyntaxError`
- `RangeError`






---
# The DOM

##### **Event Delegation**
**Event delegation** is a technique where you attach **one event listener** to a **parent element** instead of adding listeners to multiple child elements.

Because events **bubble up** the DOM, the parent can “catch” events from its children.



---
# Web Apps an HTTP

#### HTTP REQUEST vs RESPONSE: Headers & Body
Every HTTP communication has **two major parts**:
1. **Headers** → metadata (instructions, identifiers, settings)
2. **Body** → actual data being sent (if any)

#### HTTP Request (browser → server)
A request is what the **client sends**.

##### **Request HEADERS**
Contain **metadata ABOUT the request**, such as:

**Identification / Routing**
- `Host` → domain name of the server
- `User-Agent` → what browser/system is making the request
- `Accept` → what formats the client can parse (`application/json`)
- `Accept-Language` → preferred language
- `Cookie` → session/cookie data sent to server

**Security / Credentials**
- `Authorization: Bearer <token>` → if using JWT
- `Cookie: connect.sid=abc123` → session-based auth
- `Origin` / `Referer` → CORS and CSRF purposes

**Body Information**
- `Content-Type` → format of the body
    - `application/json`
    - `application/x-www-form-urlencoded`
    - `multipart/form-data`
- `Content-Length` → size of the body in bytes

**Caching**
- `If-None-Match`
- `Cache-Control`

**Example Request HEADER**
```
GET /dashboard HTTP/1.1
Host: example.com
User-Agent: Firefox/115
Accept: text/html
Cookie: connect.sid=s%3A90asf09asf09a
```


#### **Request BODY**
Used **only for methods that send data** (POST, PUT, PATCH).  
Not used for GET requests.

Contains the **actual content** the client wants to send the server, e.g.:
- Login info
- Form submissions
- JSON data
- Uploaded files

**Example JSON body**
```
{ "email": "matt@example.com", "password": "test123" }
```

#### **Request body characteristics**
- The body is **optional**
- Must match the `Content-Type` header
- Server reads it using middleware (`express.json()`)



#### **HTTP Response (server → browser)**
A response is what the **server sends back**.

##### **Response HEADERS**
Contain metadata ABOUT the response, such as:

**Status Information**
- `Status: 200 OK`
- `Status: 404 Not Found`
- `Status: 500 Internal Server Error`

**Session / Cookies**
- `Set-Cookie: connect.sid=abc123; HttpOnly; Secure`  
    (This creates or updates cookies in the browser)

**Content Information**
- `Content-Type: application/json`
- `Content-Length: 1024`

**Caching**
- `Cache-Control: no-cache`

**CORS**
- `Access-Control-Allow-Origin: *`
- `Access-Control-Allow-Credentials: true`

**Example Response HEADER**:
```
HTTP/1.1 200 OK
Content-Type: application/json
Set-Cookie: connect.sid=s%3A90asf09asf; HttpOnly; Path=/
```


##### **Response BODY**
This contains the **actual data returned to the client**, such as:
- HTML page
- JSON API response
- Error message
- Template-rendered content
- Binary data (images, files)

Example Response Body(JSON):
```
{ "message": "Login successful", "user": { "id": 10 } }
```


Example Response Body(HTML):
```
<h1>Welcome Back!</h1>
```



#### **Summary Table**

|Part|Used By|Contains|Examples|
|---|---|---|---|
|**Request Header**|Client → Server|Metadata about request|Host, Cookie, User-Agent, Content-Type|
|**Request Body**|Client → Server|Data being sent TO server|JSON, form data, file upload|
|**Response Header**|Server → Client|Metadata about response|Set-Cookie, Content-Type, Status|
|**Response Body**|Server → Client|Actual returned content|HTML, JSON, file|









---
# Client and Server Architecture



# Asynchronous Callback Programming



# Callback Hell



# AJAX



# Async and Promises

A Promise is a built-in JavaScript object that represents the eventual result (or failure) of an asynchronous operation.  
It is both a concept and a data type: it stores state, value, and callbacks and allows chaining with `.then()` and `.catch()`.


```
const p = new Promise((resolve, reject) => {});
console.log(typeof p); // "object"

Promise {
  state: "pending",
  value: undefined,
  handlers: []
}
```



# NodeJS and NPM



# Template Engines



# Express



# RESTful Design




---
# Authentication, Authorization, and Sessions

#### Authentication
- Confirms _who_ the user is.
- Usually done via:
    - Username/password
    - Session token / cookie
    - OAuth login (Google, GitHub)
    - JWT (JSON Web Tokens)
- If authentication fails → server returns:
    - **401 Unauthorized**

#### Authorization
- Determines what an authenticated user is _allowed_ to do.
- Examples:
    - User can view their own profile but not others.
    - Admins can delete items.
- If authorization fails → server returns:
    - **403 Forbidden**


#### Cookies (client-side storage used for sessions)

##### What cookies are
- Small text data stored **in the browser**, not the server.
- Sent **automatically** with every HTTP request to matching domain/path.

##### Where cookies live
- In the user's browser storage
- NOT in RAM or in server memory
- Not stored in Node.js unless using sessions to map them to server memory

##### What cookies typically store
- A **session ID** (like: `sessionId=adf9302930afsd8923`)
- User preferences (theme, language)
- JWT tokens (if using stateless auth)
- Tracking IDs
- CSRF tokens (for security)

##### Cookies should **NOT** store:
- Passwords
- Sensitive data in plain text
- Large objects (size limit ~4 KB)

##### How cookies are created (header-level overview)
When the server creates a session, it sends a cookie to the browser using:

**HTTP Response Header (server → browser)**
```
Set-Cookie: sessionId=abc123; HttpOnly; Secure; Max-Age=3000; Path=/; SameSite=Lax
```
Browser stores the cookie automatically


Then, on _every request_, the browser sends:
**HTTP Request Header (browser → server)**
```
Cookie: sessionId=abc123
```
This header tells the server:  
“Here is my stored session identifier. Please look it up.”


#### **Sessions (server-side storage)**

##### What is a session?
- A **server-side memory object** that stores information about a specific user.
- Cookie = only holds the **session ID**
- Session store = holds the actual **user data**

##### Where sessions can be stored
- In-memory store (default)
- Redis (common for production)
- MongoDB (via connect-mongo)
- SQL databases

##### **What sessions store**
Typically:
```
{
  sessionId: "abc123",
  userId: "6430acdf21",
  isLoggedIn: true,
  role: "admin",
  cart: ["item1", "item2"],
  csrfToken: "930adsf023"
}
```

##### How they are generated
1. User logs in → server validates credentials.
2. Server creates a **session object**.
3. Server stores it in the session store.
4. Server sends cookie with `sessionId` to browser.
5. Browser sends that cookie back on every request.
6. Server retrieves the session by ID and identifies the user.









---

# MongoDB



# Mongoose
Mongoose is an **ODM** (Object Data Modelling) library for **MongoDB + Node.js**.
> 	**It provides schemas, models, validation, middleware/hooks, and helpers for interacting with MongoDB in a structured way.**

MongoDB itself is schema-less, but **Mongoose lets you define schemas** for consistency and validation.

#### **What Mongoose Does**
**Adds structure to MongoDB through Schemas**
Define fields, types, required properties, default values.

**Handles validation before data is saved**
Required fields, type checking, custom validators.

**Provides Models that wrap MongoDB collections**
Model = constructor function + query interface (`find`, `save`, etc.).

**Provides middleware (hooks)**
`pre` and `post` hooks for actions like save, update, validate.

**Gives helper methods**
`.findOne()`, `.findById()`, `.updateOne()`, `.deleteOne()`, `.populate()`, etc.

**Converts JS objects to BSON behind the scenes**
You never have to manually handle BSON.


#### **Basic Setup**
**Install:**
```
npm install mongoose
```

**Connect:**
```
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost:27017/mydb")
  .then(() => console.log("Connected!"))
  .catch(err => console.error(err));
```

**Connection Errors**
- **ECONNREFUSED** → server offline
- **MongoServerSelectionError** → cannot reach DB
- **NetworkError** → firewall/connection issue

Failure to connect often causes the API to return **500** or **503**.


#### **Schemas**
A **Schema** defines the **shape** of documents in a collection.

**Example:**
```
const userSchema = new mongoose.Schema({
  name: { type: String, required: true },
  age: { type: Number, min: 0 },
  email: { type: String, unique: true },
  createdAt: { type: Date, default: Date.now },
});
```

**Schema Capabilities**
Type enforcement
If `age` is supposed to be a number, passing a string will produce a **CastError**.

Validation
- `required`
- `min` / `max`
- `enum`
- custom validators

Default values
If no `createdAt` is provided, Mongoose fills it.

Indexes
`unique: true` creates an index:
- Duplicate insert → **MongoDB 11000 Duplicate Key error**  


#### **Models**
A Model is created from a Schema:
```
const User = mongoose.model("User", userSchema);
```

**Models:**
- Act like constructors
- Represent a MongoDB collection
- Allow CRUD operations

model name `"User"` → collection name `users`  
(Mongoose automatically pluralizes)


#### **Creating and Saving Documents**
```
const user = new User({
  name: "Matt",
  age: 22,
  email: "matt@example.com"
});

await user.save();
```

**What happens internally:**
1. Mongoose validates the data
2. Converts JS object to MongoDB BSON
3. Sends insert request to MongoDB
4. MongoDB stores the document

**Common Errors:**
- **ValidationError** → missing required field
- **CastError** → wrong type
- **11000 Duplicate Key** → unique index violation


#### **Queries (Find, Create, Update, Delete)**
##### Find
Find All:
```
User.find();
```

Find One:
```
User.findOne({ name: "Matt" });
```

Find by ID:
```
User.findById("670acdf123...");
```
If ID is invalid → **CastError: ObjectId**

##### Updating
Update One:
```
User.updateOne({ name: "Matt" }, { age: 25 });
```

**Find by ID and Update:**
```
User.findByIdAndUpdate(id, { age: 26 }, { new: true });
```
The `new: true` option returns the updated doc.

By default, Mongoose does **not** run validators on updates.  
To enable:
```
User.updateOne(filter, update, { runValidators: true });
```

##### Deleting
```
User.deleteOne({ _id: id });
User.findByIdAndDelete(id);
```



#### **Schema Methods and Statics**
**Instance Method:**
```
userSchema.methods.greet = function() {
  console.log("Hello " + this.name);
};
```

```
const user = await User.findOne();
user.greet();
```


**Static Method:**
```
userSchema.statics.findByEmail = function(email) {
  return this.findOne({ email });
};
```

```
User.findByEmail("matt@example.com");
```
Useful for encapsulating logic.


#### **Virtuals**
Not stored in DB — computed on the fly.
```
userSchema.virtual("info").get(function() {
  return `${this.name} (${this.age})`;
});
```

Usage:
```
const u = await User.findOne();
console.log(u.info); // "Matt (22)"
```


#### **Middleware (“Hooks”)**
Hooks allow code to run before or after certain actions.

**Pre-Save:**
```
userSchema.pre("save", function(next) {
  console.log("Saving user...");
  next();
});
```

**Post-Save:**
```
userSchema.post("save", function(doc) {
  console.log("Saved:", doc._id);
});
```

**Types of middleware:**
- `validate`
- `save`
- `remove`
- `find`
- `findOne`
- `updateOne`
- `findByIdAndUpdate`

Note: 
`pre` receives `next`; `post` receives the doc or query result.


#### **Population (JOIN-like feature)**
When referencing documents, use population:

**Schema:**
```
const postSchema = new mongoose.Schema({
  title: String,
  author: { type: mongoose.Schema.Types.ObjectId, ref: "User" }
});
```

**Query:**
```
Post.find().populate("author");
```
Mongoose replaces the `author` ObjectId with the actual User document.


#### **Timestamps**
```
const schema = new mongoose.Schema({
  name: String
}, { timestamps: true });
```
Adds:
- `createdAt`
- `updatedAt`

Automatically.


#### **Mongoose Error Types (Exam Essential)**
**ValidationError**
Invalid data (missing required, etc.)

**CastError**
Invalid ObjectId or wrong type

Example:
```
User.findById("not-an-id");
```

**MongoServerError 11000**
Duplicate key (unique index)

**MongoNetworkError**
DB offline or unreachable

**MongoServerSelectionError**
Cannot select a server in the cluster


#### **Example End-to-End Flow**
1. User submits form → Express receives POST
2. Express reads data (`req.body`)
3. Create Mongoose model instance
4. Mongoose validates data
5. Mongoose sends insert request to MongoDB
6. MongoDB returns success or an error
7. Express sends response to client (200, 201, 400, or 500)



# WebSockets

WebSockets provide a **full-duplex**, **persistent**, **bi-directional** communication channel between client and server over a single TCP connection.

In simpler terms:
> **HTTP is request → response.  
> WebSockets allow server ↔ client messaging at any time without reloading.**


#### **Why WebSockets Exist**
HTTP is:
- stateless
- request/response only
- client must always initiate

WebSockets solve these problems by enabling:
- persistent connection
- low-latency communication
- server can send data whenever it wants
- no repeated HTTP overhead


#### **How a WebSocket Connection Starts**
WebSockets **START as an HTTP connection**, then **UPGRADE** to the WebSocket protocol.

**Step 1:** Client sends an HTTP GET request with upgrade headers:
```
GET /chat HTTP/1.1
Host: example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Sec-WebSocket-Version: 13
```

**Step 2:** Server responds with a 101 Switching Protocols:
```
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
```

After this moment → **HTTP is no longer used**.  
They are now speaking the **WebSocket protocol**.


#### **Key WebSocket Concepts**
**Full-duplex**
Client and server can send messages **independently and simultaneously**.

**Persistent**
Connection stays open until one side closes it.

**Event-driven**
JS uses events like:
- `onopen`
- `onmessage`
- `onerror`
- `onclose`

**Binary or Text frames**
WebSockets send data in _frames_, not HTTP responses.



#### WebSocket Client Syntax (Browser)
```
const socket = new WebSocket('ws://localhost:8080');

// When connection opens
socket.onopen = () => {
  console.log("Connected!");
  socket.send("Hello server!");
};

// When message arrives
socket.onmessage = event => {
  console.log("Received:", event.data);
};

// Error handling
socket.onerror = err => {
  console.error("Socket error:", err);
};

// Server closed connection or network down
socket.onclose = () => {
  console.log("Connection closed");
};
```

**Method summary:**
- **send(data)** → send text or binary data
- **close()** → close connection
- WebSockets use ws:// or wss://
- wss:// = secure (like HTTPS)
- Messages come through `event.data`

#### Events
**socket.onopen**
Triggered when connection is established.
```
socket.onopen = () => {
  console.log("Connected");
};
```


**socket.onmessage**
Triggered when the server sends a message.
```
socket.onmessage = (event) => {
  console.log("Message:", event.data);
};
```


**socket.onerror**
Triggered if a connection error occurs.
```
socket.onerror = (err) => {
  console.error("WebSocket error:", err);
};
```


**socket.onclose**
Triggered when the socket closes.
```
socket.onclose = (event) => {
  console.log("Closed:", event.code, event.reason);
};
```





#### **WebSocket Server in Node.js (ws library)**
```
const WebSocket = require('ws');

const wss = new WebSocket.Server({ port: 8080 });

wss.on("connection", ws => {
  console.log("Client connected");

  // send message to client
  ws.send("Welcome!");

  // receive message
  ws.on("message", msg => {
    console.log("Client:", msg);
  });

  ws.on("close", () => {
    console.log("Client disconnected");
  });
});
```
This server:
- waits for connections
- sends/receives messages
- handles disconnects


#### Methods and Events
`io.on("connection", callback)`
Triggered when a client connects.
```
io.on("connection", (socket) => {
  console.log("User connected");
});
```


`socket.emit(eventName, data)`
Send event **to one client**.
```
socket.emit("message", "Hello!");
```


`io.emit(eventName, data)`
Send event **to all connected clients**.
```
io.emit("announcement", "Server is restarting");
```


`socket.on(eventName, callback)`
Listen for events from a client.
```
socket.on("chat", (msg) => {
  console.log("Chat:", msg);
});
```


`socket.broadcast.emit(event, data)`
Send message to **everyone EXCEPT the sender**.
```
socket.broadcast.emit("userJoined", socket.id);
```



#### **WebSocket Protocol Basics**
**Frame**
A single message unit sent over the WebSocket connection.

Types:
- text frame
- binary frame
- ping frame
- pong frame
- close frame

**Ping / Pong**
Used to detect dead connections.

**Opcode**
Indicates frame type (0x1 for text, 0x2 for binary).

**Masking**
- All frames **from client to server** MUST be masked (security rule).
- Server-to-client frames are **not masked**.


#### **WebSocket Error Handling**
**Browser errors:**
- closed connection
- refused connection (incorrect port)
- wss:// requires HTTPS context

**Node.js errors:**
- ECONNRESET
- Client disconnected
- Frame size too large
- Masking/unmasking errors







---
# Status Codes

HTTP status codes are grouped by their **first digit**:
- **1xx** → Informational
- **2xx** → Success
- **3xx** → Redirection
- **4xx** → Client errors
- **5xx** → Server errors

#### **1xx — Informational**
**100 Continue**
- Server acknowledges initial request headers
- Client should proceed with sending the body

**101 Switching Protocols**
- Used when **upgrading to WebSockets**
- Cause: Client requests upgrade (`Upgrade: websocket`) and server agrees

**102 Processing**
- Server received the request but needs more time
- Used with WebDAV

#### **2xx — Success Codes**
These indicate that the client’s request was accepted and processed.

**200 OK**
**Meaning:** Request succeeded normally.
**Causes:**
- GET returned a resource
- POST succeeded but not creating a new resource
- PUT/PATCH succeeded

**201 Created**
**Meaning:** New resource was created.
**Causes:**
- POST to `/users` successfully created a user
- Server returns new resource location in `Location:` header

**202 Accepted**
**Meaning:** Request accepted but **not completed yet**.
**Causes:**
- Long-running jobs
- Background tasks

**204 No Content**
**Meaning:** Success but no body returned.
**Causes:**
- Successful DELETE
- Successful PUT that doesn’t return data


#### **3xx — Redirection Codes**
Browser must make another request.

**301 Moved Permanently**
**Meaning:** Resource permanently moved to a new URL.
**Causes:**
- Website restructuring
- HTTP → HTTPS redirects

**302 Found / Temporary Redirect**
**Meaning:** Temporary redirect.
**Causes:**
- Login redirect
- Maintenance page

**304 Not Modified**
**Meaning:** Cached version is still valid.
**Causes:**
- Browser sends `If-Modified-Since` or `If-None-Match`
- Server says no need to download again

This improves performance.


#### **4xx — Client Errors**
**Client did something wrong** (invalid request, bad credentials, missing data, etc.)

**400 Bad Request**
**Meaning:** Server couldn’t understand the request.
**Causes:**
- Incorrect JSON structure
- Missing required fields
- Invalid query parameters
- Too-large request body

Example:
```
{ "name": "Matt", "age": }  // invalid JSON
```

**401 Unauthorized**
**Meaning:** Authentication required or failed.
**Causes:**
- Missing authentication
- Invalid password/token
- Session expired
- Cookie missing or invalid

**Important note:**  
401 = identity not proven  
403 = identity known but not allowed

**403 Forbidden**
**Meaning:** Authenticated but **not allowed** to perform the action.
**Causes:**
- Insufficient permissions
- Attempt to access admin-only resource
- Valid token but wrong role

Example:
- Logged-in user tries to access `/admin`

**404 Not Found**
**Meaning:** Resource does not exist.
**Causes:**
- Wrong URL endpoint
- Missing file
- Deleted record
- Incorrect route in Express

Example in Express:
```
app.get("/dogs")  // but client calls /dog
```

**405 Method Not Allowed**
**Meaning:** Correct URL, wrong HTTP method.
**Causes:**
- Route exists for GET but not POST
- Trying to DELETE something that doesn’t support deletion

**409 Conflict**
**Meaning:** Request conflicts with current server state.
**Causes:**
- Duplicate record
- Unique key violation (especially in MongoDB)
    - MongoDB duplicate key error number: **11000**

**413 Payload Too Large**
**Meaning:** Request body exceeds size limits.
**Causes:**
- Uploading huge files
- Sending large JSON without proper limits

**415 Unsupported Media Type**
**Meaning:** Server does not support format sent in request.
**Causes:**
- Sending XML when server expects JSON
- Wrong `Content-Type` header


#### **5xx — Server Errors**
**The server failed even though the request was valid.**

**500 Internal Server Error**
**Meaning:** Unexpected server crash.
**Causes:**
- Coding error
- Uncaught exception
- Database query failure
- Undefined variable
- Logic bug

This is the most generic error.

**501 Not Implemented**
**Meaning:** Server doesn’t support the requested functionality.
**Causes:**
- Rare; often indicates unsupported HTTP method

**502 Bad Gateway**
**Meaning:** Server received an invalid response from an upstream server.
**Causes:**
- Reverse proxy (nginx) issues
- API gateway failure

**503 Service Unavailable**
**Meaning:** Server is temporarily unavailable.
**Causes:**
- Server overloaded
- Maintenance mode
- Database offline
- MongoDB connection refused (common!)

Note:
> When MongoDB is offline or connection fails, Express apps commonly respond with **503** or **500**.

**504 Gateway Timeout**
**Meaning:** Server took too long to respond.
**Causes:**
- Slow database
- API upstream timeout
- Infinite loops


| Code | Category | Meaning           | Common Cause           |
| ---- | -------- | ----------------- | ---------------------- |
| 200  | Success  | OK                | Request succeeded      |
| 201  | Success  | Created           | POST creating resource |
| 204  | Success  | No Content        | DELETE success         |
| 301  | Redirect | Moved Permanently | URL changed            |
| 302  | Redirect | Temporary         | Login redirect         |
| 304  | Redirect | Cache unchanged   | Cached content         |
| 400  | Client   | Bad Request       | Invalid JSON/data      |
| 401  | Client   | Unauthorized      | No/invalid auth        |
| 403  | Client   | Forbidden         | Not allowed            |
| 404  | Client   | Not Found         | Wrong endpoint         |
| 409  | Client   | Conflict          | Duplicate key          |
| 413  | Client   | Payload Too Large | Big upload             |
| 415  | Client   | Unsupported Media | Wrong Content-Type     |
| 500  | Server   | Internal Error    | Crash/exceptions       |
| 503  | Server   | Unavailable       | Server/DB offline      |
| 504  | Server   | Timeout           | Upstream slow          |
