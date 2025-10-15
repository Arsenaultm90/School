#### Process Concept

**Program** = passive entity on disk (executable file).
**Process** = active entity (program in execution).
	A process consists of:
	    - **Text section** → program code.
	    - **Data section** → global variables.
	    - **Stack** → function parameters, return addresses, local variables.
	    - **Heap** → dynamically allocated memory.
	    - **Current activity** → program counter + CPU registers.

**Key Takeaway**:  
A process = program + execution state + resources.


---
#### Process States

- **New** → being created.
- **Running** → instructions executing.
- **Waiting** → waiting for event (I/O, signal).
- **Ready** → waiting for CPU.
- **Terminated (Zombie)** → finished execution.

**Key Takeaway**:  
Processes move between **ready, running, waiting** until they terminate.


---
#### Process Control Block (PCB)

- Data structure OS uses to manage processes.  
    Contains:
	- Process state
	- Program counter
	- CPU registers
	- Scheduling info (priority, queue pointer)
	- Memory info
	- Accounting info (time, resources used)
	- I/O status (open files, devices).

**Key Takeaway**:  
PCB = "identity card" of a process; required for context switches.


---
#### Threads

- A process traditionally has **one thread of execution**.
- Threads = multiple program counters inside one process.
- Enable concurrent execution within same process.

**Key Takeaway**:  
Threads = lightweight processes within a process, share code & data but run independently.


---
#### Process Scheduling

- **Scheduler** selects next process for CPU.
- **Queues**:
    - Ready queue → waiting for CPU.
    - Wait queue → waiting for event (I/O, signal).
- Processes migrate between queues.

**Key Takeaway**:  
Scheduling ensures CPU is used efficiently by managing ready & waiting processes.


---
#### Context Switch

- Switching CPU from one process to another.
- Save old process state (PCB), load new one.
- **Overhead** → no useful work done during switch.
- Hardware support (multiple register sets) can speed it up.

**Key Takeaway**:  
Context switch = pause/resume processes; costly, so OS minimizes them.

---
#### Process Operations

 **Creation:**
- **Parent** creates child → forms tree.
- **UNIX**:
    - `fork()` → duplicate process.
    - `exec()` → replace process memory with new program.
    - `wait()` → parent waits for child.

**Termination:**
- `exit()` → process finishes.
- Parent can `abort()` child.
- Orphans/zombies if termination not handled.

**Key Takeaway**:  
Processes are created with `fork/exec`, terminated with `exit/abort`, managed via `wait`.

**Zombie Process:**
A process that has finished execution but still has an entry in the process table because its parent has _not yet called `wait()`_.

**Orphan Process:**
A process whose parent has _terminated_ **before** it (the child) finishes.

---
#### Interprocess Communication (IPC)

- **Independent vs. Cooperating processes**.
- Reasons: info sharing, computation speedup, modularity, convenience.
- Models:
    - **Shared memory** → fast, but needs synchronization.
    - **Message passing** → safer, easier for distributed systems.

**Producer-Consumer Problem**
- Classic IPC example.
- Unbounded buffer: producer never waits.
- Bounded buffer: producer must wait if full.

**Key Takeaway**:  
IPC enables cooperation; choice depends on performance vs. safety.

**Shared Memory**
- Processes share a memory segment.
- Synchronization handled by processes, not OS.
- Very fast but requires careful synchronization.

**Message Passing**
- Send/receive messages, no shared variables.
- Works across networked systems.
- Communication link properties: direct vs. indirect, sync vs. async, buffered vs. unbuffered.
-  Safer and more portable than shared memory, but slower.

**Direct vs. Indirect Communication**
- **Direct**: processes name each other explicitly (`send(P, msg)`).
- **Indirect**: via mailbox/port (`send(A, msg)` → mailbox).
- Direct = one-to-one; indirect = more flexible (mailboxes).

**Synchronization in IPC**
- **Blocking (synchronous)** → sender/receiver wait.
- **Non-blocking (asynchronous)** → sender/receiver continue immediately.
- **Rendezvous** → both blocking, meet exactly once.
- Sync choice affects responsiveness and complexity of IPC.

**Buffering in IPC**
- **Zero capacity** → no queue, must rendezvous.
- **Bounded capacity** → finite queue, sender waits if full.
- **Unbounded capacity** → infinite queue (theoretical).
- Buffering = temporary storage for messages in IPC,


---
#### Pipes

- Unidirectional or bidirectional communication channels.
- **Ordinary pipes**: parent-child, unidirectional.
- **Named pipes**: bidirectional, unrelated processes, multiple users.

**Key Takeaway**:  
Pipes are simple IPC for producer-consumer; named pipes extend use beyond parent-child.


---
#### Summary

1. **Program → Process**
    - A program on disk becomes an executing **process** once loaded into memory.
2. **Process → PCB + Process States**
    - Each process is tracked by a **Process Control Block (PCB)** and moves between states (New, Ready, Running, Waiting, Terminated).
3. **PCB + States → Scheduling & Context Switch**
    - The OS uses the PCB info to **schedule processes** on the CPU.
    - Context switching lets the OS move the CPU between processes.
4. **Scheduling → Threads**
    - Threads extend processes by allowing multiple execution paths within one process.
5. **Process → Creation & Termination**
    - Processes form parent-child relationships, and can be created (fork/exec) or terminated (exit, abort).
6. **PCB → Special Cases**
    - Mobile OS (Android/iOS) and multiprocess apps (Chrome) manage processes differently.
7. **Scheduling → IPC (Inter-Process Communication)**
    - When processes need to cooperate, they communicate via **Shared Memory** or **Message Passing**.
8. **IPC → Synchronization & Buffering**
    - IPC requires synchronization (blocking vs. non-blocking) and buffering (queues, pipes).



![[Pasted image 20250918074203.png|500]]
- **New → Ready**: Process created, waiting to be scheduled.
- **Ready → Running**: CPU scheduler picks the process.
- **Running → Waiting**: Process requests I/O or event.
- **Waiting → Ready**: I/O or event completed.
- **Running → Ready**: Preemption (time slice expired, higher-priority process ready).
- **Running → Terminated**: Process finishes execution.
