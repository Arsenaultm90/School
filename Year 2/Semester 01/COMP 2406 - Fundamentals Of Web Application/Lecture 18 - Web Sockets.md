**WebSockets** are a communication protocol that provides a **persistent**, **full-duplex** (two-way), **real-time** connection between a **client (browser)** and a **server**.

Unlike HTTP (which is request → response only), WebSockets allow **both sides** to send data **at any time** without re-establishing connections.


HTTP has limitations:
- It’s **stateless**
- It’s **one-directional** (client must request, server responds)
- It requires repeated connections (polling, long-polling)

WebSockets solve all of these:
- The connection stays open
- Server can push data whenever it wants
- Extremely low latency
- Ideal for real-time applications


#### How WebSockets Work (High Level)
1. **Client sends an HTTP request with “Upgrade: websocket”**
2. **Server accepts and “upgrades” the connection**
3. A persistent TCP connection is established
4. Both sides can now send messages freely:
    - server → client
    - client → server

No more HTTP headers, no repeated requests.


#### WebSocket Lifecycle

|Event|Meaning|
|---|---|
|`open`|Connection established|
|`message`|A message was received|
|`close`|Connection closed|
|`error`|Something went wrong|



---
# Syntax

**Create a socket**
```
const socket = new WebSocket("ws://localhost:3000");
```

**When connection opens**
```
socket.onopen = () => {
  console.log("Connected to server");
  socket.send("Hello!");
};
```

**Listen for messages**
```
socket.onmessage = (event) => {
  console.log("Message from server:", event.data);
};
```

**Handle Errors**
```
socket.onerror = (err) => {
  console.log("WebSocket error:", err);
};
```

**Close connection**
```
socket.onclose = () => {
  console.log("Connection closed");
};
```



#### Node.js WebSocket Server

**Install**
```
npm install ws
```

**Server Code**
```
const WebSocket = require("ws");

const server = new WebSocket.Server({ port: 3000 });

server.on("connection", (socket) => {
  console.log("Client connected");

  socket.send("Welcome!");

  socket.on("message", (data) => {
    console.log("Client says:", data);
    socket.send("You said: " + data);
  });

  socket.on("close", () => {
    console.log("Client disconnected");
  });
});
```



---
# WebSocket Message Types

WebSockets can send:
- **Strings**
- **JSON**
- **Binary (ArrayBuffer, blobs)**

Example sending JSON:
```
socket.send(JSON.stringify({ type: "chat", message: "Hello" }));
```

Receiving JSON:
```
socket.onmessage = event => {
  const data = JSON.parse(event.data);
};
```

