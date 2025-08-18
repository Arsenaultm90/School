#### **Introduction to IPC: Signals vs. Sockets**

Inter-Process Communication (IPC) allows processes to exchange data. **Signals** are a simple form of IPC, limited to sending single integers between processes on the same machine. They are often used for low-level system tasks, such as interrupting a process during errors. However, their functionality is restricted—only two user-defined signals are available, making them unsuitable for complex communication.

In contrast, **sockets** provide a more powerful and flexible method for IPC. They enable processes to communicate not only on the same machine but also across different hosts over a network. Unlike signals, sockets can transmit any type of data, making them ideal for applications like web servers, messaging apps, and distributed systems.

---
#### **Understanding Sockets**

A **socket** is an endpoint for communication, acting like a virtual "plug" that connects processes. Each socket is uniquely identified by:
- An **IP address**, which specifies the host on a network.
- A **port number**, which identifies the specific application on that host.
    

When combined, these components allow data to be routed accurately between applications, even across different machines. Sockets abstract the complexities of network communication, providing a standardized way for programs to send and receive data.

---
#### **Transport Layer Protocols: TCP and UDP**

Sockets rely on transport layer protocols to manage data transmission. The two most common protocols are:

1. **TCP (Transmission Control Protocol)**
    - Uses **stream sockets**, which are connection-oriented.
    - Before communication begins, a connection is established between the sender and receiver, ensuring reliability.
    - Features:
        - Guaranteed delivery (retransmits lost packets).
        - Correct packet order (reassembles data in the right sequence).
        - Error checking (detects and corrects corrupted data).
    - Ideal for applications where accuracy is critical, such as file transfers or web browsing.
        
2. **UDP (User Datagram Protocol)**
    - Uses **datagram sockets**, which are connectionless.
    - Data is sent immediately without establishing a connection, making it faster but less reliable.
    - Features:        
        - Low overhead (no connection setup or error recovery).
        - No guarantee of delivery, order, or correctness.
    - Best suited for real-time applications like video streaming or online gaming, where speed matters more than perfect accuracy.
        

There are also **raw sockets**, which bypass the transport layer entirely, allowing direct interaction with network protocols. These are typically used for specialized tasks like network diagnostics or custom protocol implementations.

---
#### **Client-Server Model**

Sockets are commonly used in the **client-server architecture**, where:
- The **server** waits for incoming requests and processes them.
- The **client** initiates requests and receives responses.

**TCP Communication Steps:**
1. **Server Side:**
    - Creates a socket and binds it to an IP and port.
    - Listens for incoming connections.
    - Accepts a client connection and exchanges data.
    - Closes the socket when done.

2. **Client Side:**
    - Creates a socket and connects to the server.
    - Sends/receives data.
    - Closes the connection.

**UDP Communication Steps:**  
Since UDP is connectionless, the process is simpler:
- The server binds a socket and waits for messages.
- The client sends data directly without establishing a connection.
- Both sides use `sendto()` and `recvfrom()` to exchange datagrams.

---
#### **Key Functions and Structures**

To work with sockets in C, several functions and data structures are essential:
- **Functions:**
    - `bind()`: Associates a socket with an address and port.
    - `listen()`: Prepares a TCP socket to accept connections.
    - `accept()`: Establishes a connection with a client.
    - `connect()`: Client-side function to initiate a TCP connection.
    - `send()`/`recv()`: Used in TCP for reliable data transfer.
    - `sendto()`/`recvfrom()`: Used in UDP for connectionless communication.
    - `select()`: Monitors multiple sockets for activity (useful for UDP servers).

- **Data Structures:**
    - `sockaddr_in`: Stores socket address details (IP, port, protocol family).
    - Byte order functions (`htons()`, `htonl()`, etc.): Ensure proper formatting of network data.

---
#### **Signals vs. Sockets: When to Use Each**

- **Signals** are best for simple, same-machine notifications (e.g., interrupting a process).
- **Sockets** are ideal for complex, cross-machine communication (e.g., web servers, multiplayer games).

While signals are lightweight and fast, their limitations make them unsuitable for most modern IPC needs. Sockets, though more complex, provide the versatility required for networked applications.

---
#### **Conclusion**

Sockets are a foundational concept in networking and IPC, enabling everything from local process communication to global internet applications. Understanding the differences between **TCP** (reliable, connection-based) and **UDP** (fast, connectionless) is crucial for designing efficient systems. By mastering socket programming, you can build robust client-server applications that handle data transmission seamlessly.