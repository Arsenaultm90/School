**System Calls**
- **Definition**: Requests made by a program to the operating system kernel to perform low-level operations.
- **Purpose**: Allow user-level programs to access hardware and OS resources safely.
- **Examples**: `read()`, `write()`, `fork()`, `exec()`, `open()`, `close()`

A process can fork to create a new process.  
**Fork:** 
	Make an identical copy of the current process, but with a new process ID and a separate memory space.  

This child process can then morph into a different program.  

**Morph:** 
	Change the program being executed by the process, while keeping the same process ID but the memory space is replaced with the new program’s memory


---
#### Process, Thread, and Control Flow

**Defining a Process**  
	Program: Set of instructions stored in a file.  
	Process: Program executing with its own memory and time with the CPU.  
	Process has an ID (pid) and parent process (ppid)  
	Tree structure: Each process is spawned by another process

**Defining a Thread, Control Flow**  
	Control Flow: The sequence of instructions executed by a process.  
	Registers storing the next instruction to execute, where the stack is, etc.  
	Thread: A control flow within a process.  
	One stack, one set of registers



---
#### Concurrent Programming

##### Types of Concurrent Systems

**Distributed Systems**
	**Definition**: Multiple computers (nodes) working together over a network.
	**Features**:
	    - Each node has its own memory and processor.
	    - Communicate using message passing (e.g., sockets, RPC).
	**Examples**: Web servers, cloud computing, microservices.

**Multi-Process Systems**
	**Definition**: One computer running multiple independent processes.
	**Features**:
	    - Each process has its own memory space.
	    - Communication via inter-process communication (IPC): pipes, shared memory, message queues.
	**Examples**: Unix shell spawning processes, web browsers running tabs in separate processes.

**Multi-Threaded Systems**
	**Definition**: A single process with multiple threads sharing the same memory.
	**Features**:
	    - Threads share global memory but have individual stacks.
	    - Communication is easier (shared memory), but requires synchronization.
	**Examples**: Video games, GUI applications, server handling multiple connections.

|Feature|Distributed|Multi-Process|Multi-Threaded|
|---|---|---|---|
|Memory|Separate per node|Separate per proc|Shared|
|Communication|Network|IPC|Shared variables|
|Fault Tolerance|High|Medium|Low|
|Performance|Slower|Medium|Faster|
|Complexity|High|Medium|High (due to sync)|

##### Concurrency Issues And Deadlocks

**Common Concurrency Issues** 
**Race Conditions**
- **Occurs when** multiple threads/processes access shared data at the same time and the final result depends on the sequence of execution.
- **Solution**: Use mutexes, locks, atomic operations.

**Starvation**
- **Occurs when** a thread/process is perpetually denied access to resources.
- **Example**: A low-priority thread never gets scheduled.

**Livelock**
- **Occurs when** threads keep changing state in response to each other without making progress.


**Deadlocks**
**Definition**
A situation where a group of threads or processes are blocked forever, each waiting for a resource held by another.

**Necessary Conditions (Coffman’s Conditions)**:
1. **Mutual Exclusion**: At least one resource must be held in a non-shareable mode.
2. **Hold and Wait**: A process holding one resource is waiting to acquire additional resources.
3. **No Preemption**: Resources cannot be forcibly taken.
4. **Circular Wait**: A circular chain of processes exists, each waiting for a resource held by the next.

**Deadlock Prevention**
- Avoid one of Coffman's conditions (e.g., use all resources at once, allow preemption).

**Deadlock Avoidance**
- Use algorithms like **Banker's Algorithm** to ensure safe resource allocation.

**Deadlock Detection and Recovery**
- Detect cycles in resource allocation graph.
- Kill or restart processes to break deadlock.