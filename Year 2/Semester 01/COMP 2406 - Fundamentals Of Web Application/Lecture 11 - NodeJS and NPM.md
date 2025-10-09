#### **NodeJS**

**Node.js** is a **JavaScript runtime environment** that allows you to run JavaScript code **outside the browser**, typically on a **server**.

- It uses **Google’s V8 JavaScript engine** (the same one Chrome uses) to compile JS code directly into **machine code**.
- It is **event-driven**, **non-blocking**, and **asynchronous** — making it ideal for **I/O-heavy**, **real-time applications** (like chat apps, APIs, streaming services, etc.).


##### Key Features
1. **Asynchronous and Non-Blocking I/O**
	- Node uses **non-blocking I/O operations**, meaning it can handle multiple operations **without waiting** for previous ones to finish.
	- Instead of waiting for a file read or DB query, Node moves on to other tasks and uses **callbacks**, **Promises**, or **async/await** to handle results later.
	- "I/O" refers primarily to interaction with the system's disk and network supported by [libuv](https://libuv.org/).

2. **Single-Threaded Event Loop**
	- Although Node runs on a **single thread**, it can handle **many concurrent connections**.
	- It achieves this through an **event loop**, which offloads blocking operations to the **libuv thread pool** and responds to events asynchronously.

3. **Built on the V8 Engine**
	- Node uses Chrome’s **V8 engine**, written in C++, for fast execution.
	- V8 converts JavaScript into **native machine code**, making Node extremely fast.

4. **Event-Driven Architecture**
	- Everything in Node revolves around **events** (e.g., “data received,” “file read complete”).
	- Node’s **EventEmitter** class allows custom events to be defined and handled efficiently.
    
5. **Cross-Platform**
	- Node.js runs on **Windows, macOS, Linux**, and other platforms with minimal setup.
    
6. **Rich Package Ecosystem (npm)**
	- Node uses **npm (Node Package Manager)**, which has **millions of reusable packages**.
	- Makes development much faster and easier.
    
7. **Scalable**
	- Suitable for **microservices**, **real-time systems**, and **RESTful APIs** due to its lightweight and non-blocking design.


##### Behind The Scenes
1. **Event Loop and Single Thread**
	- Node runs a **single main thread**.
	- The **event loop** continuously checks for pending events or callbacks to execute.
	- This design avoids the overhead of managing multiple threads.
    
2. **libuv**
	- A C library that provides **asynchronous I/O** and a **thread pool** under the hood.
	- Handles file system access, network operations, DNS lookups, etc.

3. **Worker Pool (Thread Pool)**
	- Heavy operations (like file reads, crypto, or compression) are sent to a **pool of threads** managed by `libuv`.
	- Once done, results are sent back to the event loop via callbacks.

4. **Callback Queue**
	- Completed asynchronous tasks get added to the **callback queue**.
	- The event loop checks this queue and executes the callbacks one by one.

5. **Event Emitter**
- Node’s core is event-driven.  
    Example:
```
const EventEmitter = require('events');
const emitter = new EventEmitter();

emitter.on('greet', () => console.log('Hello!'));
emitter.emit('greet');
```

6. **Modules and CommonJS**
	- Node uses **CommonJS modules** (with `require` and `module.exports`).
	- In newer versions, it also supports **ES Modules (ESM)** syntax using `import/export`.

7. **V8 Engine**
	- Executes JS code efficiently by converting it to native machine code using **JIT (Just-In-Time)** compilation.



---
#### Modules

In Node.js, **a module** is simply **a reusable block of code** whose existence **does not accidentally impact other code**.  
Each file in Node.js is treated as a **separate module**.
The module.exports object represents the values/functions/objects that this module exposes. 
Essentially, it is the object returned when you ‘require’ the module from somewhere else.

Node.js has **three** types of modules:
1. **Core (Built-in) Modules**
2. **Local (User-defined) Modules**
3. **Third-party Modules** (via NPM)

**Core Modules**
These come **pre-installed** with Node.js — no need to install separately.

Examples:
- `fs` — File system operations
- `http` — Create servers and handle HTTP requests
- `path` — Work with file paths
- `os` — Access system info
- `events` — EventEmitter class
- `crypto` — Encryption and hashing

Usage:
```
const fs = require('fs');
fs.writeFileSync('hello.txt', 'Hello world!');
```

**Local Modules** (User-Defined)
These are **your own JavaScript files**.  
You create them to organize and reuse code.

Example:
```
// calculator.js
exports.add = (a, b) => a + b;
exports.sub = (a, b) => a - b;

// app.js
const calc = require('./calculator');
console.log(calc.add(5, 3)); // 8
```

**Third Party Modules (NPM)**
These are modules you **install using npm**.

Example:
```
// CLI
npm install express

// JS File
const express = require('express');
const app = express();

app.get('/', (req, res) => res.send('Hello from Express!'));
app.listen(3000);

```



---
#### The HTTP Module

The **`http`** module is a **core Node.js module** that allows you to:
- Create an **HTTP server**.    
- Handle **client requests** (like browsers, APIs, etc.).
- Send **HTTP responses** back to clients.
- Make **HTTP requests** to other servers (client-side of Node).

It’s **built on top of TCP** (via the `net` module) and provides a high-level interface for building web servers and clients.

To use it:
```
const http = require('http');
```


 **Creating a Simple HTTP Server**
The simplest Node.js server looks like this:
```
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello, world!\n');
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000/');
});
```
- `http.createServer()` → creates a new server.
- The callback `(req, res)` is called **every time a request is received**.
- `res.writeHead(statusCode, headers)` → sets the HTTP status code and headers.
- `res.end()` → sends the response and ends the connection.
- `server.listen(port)` → starts listening on the given port.


**The Request Object (`req`)**
When a client connects, Node passes a **`IncomingMessage`** object (`req`) into the callback.
`req` is a **readable stream**, meaning you can read incoming data from it.

Common properties:

| Property                | Description                                    |
| ----------------------- | ---------------------------------------------- |
| `req.url`               | The path part of the request (e.g. `/about`)   |
| `req.method`            | HTTP method (GET, POST, etc.)                  |
| `req.headers`           | Object containing the request headers          |
| `req.on('data', chunk)` | Fired when a data chunk arrives (for POST/PUT) |
| `req.on('end')`         | Fired when all data has been received          |

Example: Reading Request Data (Readable Stream)
Let’s say the client sends JSON data (like in a POST request):
```
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.method === 'POST') {
    let body = '';

    // Listen for data chunks
    req.on('data', chunk => {
      body += chunk.toString();
    });

    // Once all data is received
    req.on('end', () => {
      console.log('Data received:', body);
      const parsed = JSON.parse(body);
      res.writeHead(200, { 'Content-Type': 'application/json' });
      res.end(JSON.stringify({ message: 'Data received', data: parsed }));
    });
  } else {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Send a POST request with data');
  }
});

server.listen(3000);
```
- The body of the request doesn’t come in all at once — it’s streamed in small chunks.
- Node reads each chunk asynchronously.
- The `end` event fires once the stream is complete.

**Request From Client**
```
// client.js
const http = require('http');

const data = JSON.stringify({ message: 'Hello Server' });

const options = {
  hostname: 'localhost',
  port: 3000,
  path: '/',
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Content-Length': data.length,
  },
};

// Create a request object
const req = http.request(options, res => {
  console.log(`STATUS: ${res.statusCode}`);
  res.on('data', chunk => console.log('Client received:', chunk.toString()));
});

// Send data
req.write(data);
req.end();
```
1.  **Client (`http.request`)**
    - Opens a TCP connection to `localhost:3000`.
    - Writes the HTTP headers and body data to the socket (`req.write(data)`).
    - Ends the request (`req.end()`).

2. **Server (`http.createServer`)**
    - Gets the new incoming request.
    - Emits the `'data'` event **as each chunk arrives** over the socket.
    - Emits `'end'` once all chunks are received.

3. **Server responds**
    - Calls `res.writeHead()` and `res.end()` to send back data.

4. **Client receives**
    - The callback in `http.request(options, res => ...)` fires.
    - The client can listen for `'data'` and `'end'` on the **response stream**.


**The Response Object (`res`)**
The `res` parameter is an instance of **`http.ServerResponse`**.  
It’s a **writable stream** — meaning you can send data back to the client.

Common methods and properties:

|Method / Property|Description|
|---|---|
|`res.writeHead(statusCode, headers)`|Sets status code and headers|
|`res.write(data)`|Writes data to the response stream|
|`res.end([data])`|Ends the response (optionally sending last data)|
|`res.statusCode`|Get or set the HTTP status code|
|`res.setHeader(name, value)`|Set individual headers|
|`res.getHeader(name)`|Retrieve a specific header|

Example:
```
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/html' });
  res.write('<h1>Hello from Node.js</h1>');
  res.end('<p>This is a simple web server</p>');
});

server.listen(3000);
```


When you use the HTTP module:
1. Node listens for incoming connections (non-blocking I/O).
2. For each request:
    - The request data (`req`) arrives in chunks asynchronously.
    - Node buffers those chunks until `end`.
    - You process the data and write to the response (`res`).
3. Node automatically handles TCP connection details underneath.

Because everything is event-driven and asynchronous:
- Node can handle **thousands of concurrent requests** without blocking.
- Each request’s data and response flow through streams efficiently.


---
#### **NPM (Node Package Manager)**

It is the **default package manager for Node.js**, used to:
- **Install, share, and manage dependencies** (libraries, frameworks, tools) for your Node.js project.
- **Publish and distribute** your own packages.
- **Version control** and manage dependencies for projects through a configuration file (`package.json`).

> When you install Node.js, npm is installed automatically.


##### Key Features of npm
1. **Package Management**
	- Install, update, remove, and manage external libraries.
	- Handles dependency trees automatically.

2. **Version Control**
	- Supports **Semantic Versioning (SemVer)** (e.g., `^1.2.3`, `~1.2.3`).
	- Ensures compatibility and stability between versions.

3. **Online Registry**
	- npm hosts the **largest software registry in the world**, with **millions of open-source packages**.
	- The registry is available at [https://www.npmjs.com](https://www.npmjs.com)

4. **Local and Global Packages**
	- **Local:** Installed in the project directory (`node_modules/`).
	- **Global:** Installed system-wide (useful for CLI tools).

5. **Script Automation**
	- Define and run custom scripts (e.g., `npm start`, `npm test`, `npm run build`) from `package.json`.

6. **Dependency Management Files**
	- **`package.json`** → Declares project metadata and dependencies.
	- **`package-lock.json`** → Locks exact versions to ensure consistent installs across systems.


##### How NPM Works
When you run:
```
npm install express
```
1. **Checks package.json**
    - Looks for `dependencies` or `devDependencies` (if any).
    - If no package.json exists, it can still install and create one with `--save`.
2. **Queries npm Registry**
    - npm contacts the **central registry (npmjs.org)** to find the requested package.
3. **Downloads Package**
    - Fetches the latest version (or a specific version) of the package.
    - Downloads it along with **all its dependencies**.
4.  **Stores Locally**
    - Installs the package into the project’s `node_modules` folder.
    - Updates or creates `package-lock.json` for version tracking.
5.  **Updates package.json**
    - Adds the dependency under `"dependencies"` (unless `--no-save` is used).
6.  **Caching**
    - npm caches the package locally (in `~/.npm`) for faster future installations.


##### Core File
1. **package.json**
	- Defines the metadata for your project and its dependencies.
2. **package-lock.json**
	- Records the **exact version numbers** of all installed packages (including nested dependencies).    
	- Ensures deterministic builds — meaning everyone who installs your project gets identical versions.
3. **node_modules/**
	- Stores all installed dependencies.
	- Created automatically when running `npm install`.


##### Common NPM Commands

|Command|Description|
|---|---|
|`npm init`|Create a new `package.json` file interactively|
|`npm init -y`|Create a default `package.json` without prompts|
|`npm install <pkg>`|Install a package locally and add to dependencies|
|`npm install <pkg> -g`|Install a package globally|
|`npm install`|Install all dependencies listed in package.json|
|`npm uninstall <pkg>`|Remove a package|
|`npm update`|Update all outdated packages|
|`npm outdated`|List outdated packages|
|`npm list`|Display installed packages and their versions|
|`npm start`|Run the “start” script defined in `package.json`|
|`npm run <script>`|Run a custom script defined in `scripts`|
|`npm publish`|Publish your package to the npm registry|
|`npm login`|Authenticate to npm registry|
|`npm cache clean --force`|Clear npm’s local cache|


##### Local vs Global Packages

|Type|Installed Location|Usage|Example|
|---|---|---|---|
|**Local**|`project/node_modules/`|For specific project use|`npm install express`|
|**Global**|System-wide (e.g., `/usr/local/lib/node_modules`)|CLI tools, reusable commands|`npm install -g nodemon`|


##### Semantic Versioning
npm follows **Semantic Versioning** rules:  
Format → **MAJOR.MINOR.PATCH**

Example: `2.5.1`
- **2** → Major version (breaking changes)
- **5** → Minor version (new features, backward compatible)
- **1** → Patch version (bug fixes)

**Prefix symbols in package.json:**

| Symbol   | Meaning                                         |
| -------- | ----------------------------------------------- |
| `^1.2.3` | Accepts minor and patch updates (≥1.2.3 <2.0.0) |
| `~1.2.3` | Accepts only patch updates (≥1.2.3 <1.3.0)      |
| `1.2.x`  | Accepts any patch version                       |
| `*`      | Accepts any version                             |



---
#### MIME Types

- **MIME = Multipurpose Internet Mail Extensions**
- Originally used in email, now standard for the **Content-Type** in HTTP.
- Tells the **client (browser or other)** what kind of data is being sent.

Example :

|MIME Type|Meaning|
|---|---|
|`text/html`|HTML document|
|`text/css`|CSS stylesheet|
|`application/javascript`|JavaScript file|
|`application/json`|JSON data|
|`image/png`|PNG image|
|`image/jpeg`|JPEG image|
|`audio/mpeg`|MP3 audio|
|`video/mp4`|MP4 video|

