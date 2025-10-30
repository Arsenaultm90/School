Chapters 1 - 6
Content :
1. Slides
2. Book
3. Quizzes


#### **Chapter I** - System Calls, OS Structure

**System call** – 
	A controlled entry point for a user program to request OS services (like I/O, process creation, or memory management).
    
**User mode vs Kernel mode** –
- **User mode:** Limited access to hardware/resources; normal program execution.
- **Kernel mode:** Full access to hardware; runs OS services and system calls.
    
**Process management** – 
	OS service that handles creation, scheduling, synchronization, and termination of processes.
    
**I/O management** – 
	OS service that abstracts devices, buffers data, handles interrupts, and provides device-independent access.
    
**Bootloader purpose** – 
	Small program loaded by firmware (BIOS/UEFI) that loads the OS kernel into memory and starts it.
    
**Monolithic vs Layered OS:**
- Monolithic: all services in one large kernel → fast but hard to maintain.
- Layered: services split into hierarchical layers → easier to maintain, but may have overhead.
    
**Microkernel advantage** – 
	Minimizes kernel code → improved reliability; crashes in user-space services don’t crash the whole OS.
    
**Modular OS** – 
	Kernel plus loadable modules. Unlike microkernel, most services may still run in kernel space; modules can be added/removed dynamically.
    
**Hybrid OS advantage/disadvantage:**
- Advantage: Combines performance of monolithic with reliability/modularity of microkernel.
- Disadvantage: Can be complex to design and maintain.

**System call safe hardware access** – 
	System calls validate parameters, run in kernel mode, and ensure processes cannot directly access hardware, preventing conflicts or corruption.

**Device Driver -**
	A piece of hardware that operates/manages a particular device type, translating its operation into data/signal streams understandable by a CPU and vice versa.

**Notify CPU that I/O operations are done -**
	Device (via its controller) sends an interrupt to CPU.

**Interrupt Handling -**
1. **Save state** – The CPU stores the current task’s context (registers, program counter, etc.) so it can resume later.
2. **Execute handler** – The OS runs the **interrupt service routine (ISR)** to handle the event.
3. **Restore state** – After the ISR finishes, the CPU restores the saved context and resumes the interrupted task as if nothing happened.

**Interrupt-Driven I/O**
	**Characteristics:**
		- CPU actively involved in every data transfer.
		- More CPU overhead for large data transfers.
		- Faster than pure polling, but not as efficient as DMA for bulk data.

**Direct Memory Access(DMA)**
	**Characteristics:**
		- CPU is not involved in each data transfer — much **more efficient for large blocks of data**.
		- Reduces CPU overhead and speeds up system.
		- Typically used for disks, network cards, sound cards, and other high-speed I/O devices.




---
#### **Chapter II** - Processes

**Process** – A **program in execution**, with its own state, registers, stack, and memory. Unlike a program (static code on disk), a process is **active**.

**Process Control Block (PCB)** – OS data structure storing **process state, program counter, CPU registers, memory info, scheduling info, open files, and accounting info**.

**Preemptive vs Non-preemptive Scheduling:**
- **Preemptive:** OS can interrupt a running process (e.g., Round-Robin).
- **Non-preemptive:** Process runs until it terminates or waits for I/O (e.g., FCFS).

**Process State:** Current status of a process in execution. Common states: **New, Ready, Running, Waiting/Blocked, Terminated**.

**Thread vs Process:**
- Thread = lightweight execution unit within a process, shares address space.
- Process = independent execution unit with its own memory space.

**Inter-Process Communication (IPC):** Mechanism for processes to **exchange data or synchronize**, necessary because processes are isolated in memory.

**Shared-Memory vs Message-Passing IPC:**
- **Shared memory:** Processes communicate by reading/writing to a common memory segment; faster but requires synchronization.
- **Message passing:** Processes communicate by sending and receiving messages; safer but slower.

**Shared-memory IPC advantage/disadvantage:**
- Advantage: Fast data exchange.
- Disadvantage: Must explicitly synchronize to avoid race conditions.

**Message-passing IPC advantage/disadvantage:**
- Advantage: Simpler, safer (no direct memory access).
- Disadvantage: Slower due to copying messages and system calls overhead.

**Scheduling and metrics:**
- Scheduling determines **which process runs next**.
- Metrics affected: **Turnaround time** (submission → completion), **Waiting time** (time in ready queue), **Response time** (time until first CPU allocation).



---
#### **Chapter III**




---
#### **Chapter IV**

**1. Turnaround Time (TAT)**
	**Definition:** Total time taken for a process to complete, **from submission to completion**.
	- Usually measured from **arrival/admission into the ready queue** until **completion of execution**.
	- Includes:
	    - Waiting time in the ready queue
	    - Time spent executing on the CPU
	    - Time spent in I/O or other delays
	**Formula:**
		TAT = Completion Time−Arrival Time


**2. Response Time (RT)**
	**Definition:** Time from when a process is **first submitted/admitted** until it **first gets the CPU**.
	- Measures how quickly the system **responds to a process**.
	- Includes **time spent waiting in the ready queue before first execution**.
	**Formula:**
	RT = Time of first CPU allocation − Arrival Time


**3. Waiting Time (WT)**
	**Definition:** Total time a process spends in the **ready queue waiting for CPU**.
	- Does **not include** time spent executing or in I/O.
	- Can accumulate **over multiple CPU bursts** if the process is preempted multiple times.
	**Formula:**
	WT = TAT − (Total CPU time + I/O time)




---

**Process States :**
- **New** → being created.
- **Running** → instructions executing.
- **Waiting** → waiting for event (I/O, signal).
- **Ready** → waiting for CPU.
- **Terminated (Zombie)** → finished execution.

**Process Interrupted by I/O System Call:**
	Waiting -> Ready -> Executing

**Unique Transition Order:**
	The **ordering** of certain transitions is ambiguous because:
	- Interrupt handling sequence varies by implementation
	- Some transitions are logically independent (no happens-before relationship)
	- Scheduler policies introduce additional ordering flexibility
	**"The order isn't unique because there's no strict happens-before relationship between the interrupt preempting P1 and the I/O completion unblocking P0 - these are logically independent events that occur 'simultaneously' from the OS's perspective, and different implementations or observation points might record them in different orders."**

Process state transitions are _not unique_ because the exact sequence of transitions depends on how the operating system’s scheduler and I/O handling are implemented.

##### **Definitions :**
**Multiprocessing:** 
	Truly running multiple processes at the same time on separate cores.

**Multitasking:** 
	The OS makes it _appear_ that multiple programs are running at once by **rapidly switching a single CPU** between processes.

**Pre-emptive:** 
	The operating system can interrupt (or _preempt_) a currently running process **before it finishes**, so another process can use the CPU.

**Inodes store metadata:**
- File size
- Owner
- Permissions
- Timestamps
- Pointers to data blocks
**Important:** File names are stored in the **directory entry**, not in the inode.

**File Systems in Linux:**
- **File descriptor:** A small integer returned when you open a file.
- **System calls:** Used to open, read, write, and close files.
- **Inode:** Data structure that stores metadata about a file (but not its name).

**Directory Entries:**
	Directories are special files that contain a list of entries mapping filenames to inode numbers. When you access a file path, the kernel walks through each directory component, looking up each name to find its inode.

**Direct Pointers:**
	Contain pointers to blocks of memory defined by Linux. (1 read)

**Indirect Pointers:**
	A block containing pointers to memory outside the range of the direct pointers. (1 read for block + 1 read for memory)


**Liveness:**
	**Liveness** refers to a set of properties that a system must satisfy to  
	ensure processes make progress.
