# Chapter 1 -- OS Intro
- Interrupts -- what they are, stages of handling
- Kernel-vs-User modes -- what each can/cannot do and why
- Computer Architecture basics (device drivers, bus, DMA...)
- Multi-programming vs multi-processing

### **Interrupts**
**What an interrupt is:**  
A hardware-generated signal telling the CPU: _"Stop what you're doing and run this handler."_

**Stages of Interrupt Handling**
1. Device triggers interrupt line.
2. CPU finishes current instruction.
3. CPU switches to kernel mode.
4. Program counter + registers saved.
5. Interrupt handler runs.
6. Handler clears interrupt.
7. CPU restores context and returns to user process.

**Types**
- Hardware interrupts (I/O device finished work)
- Software interrupts (exceptions, traps)

### **Kernel vs User Mode**
**User mode:**
- Can NOT directly access hardware
- Can NOT modify page tables
- Must use system calls

**Kernel mode:**
- Can access hardware & memory
- Runs interrupt handlers
- Performs scheduling, memory management

**Why two modes?**  
→ Protection & stability (users can't crash the machine).

**How do we switch modes?**
Only three ways:
1. **Hardware Interrupt** (device signals the CPU → enters kernel mode)
2. **Exception** (divide by zero, page fault → kernel mode)
3. **System Call (trap)**
    - User program intentionally executes an instruction like `int 0x80`, `syscall`, or `trap`
    - CPU automatically switches to kernel mode and jumps to OS handler.

The CPU always switches back to user mode when returning from the handler.

### **Architecture Basics**
- **Device Driver:** Software that controls a specific piece of hardware.
- **Bus:** Communication path (PCIe, USB).
- **DMA (Direct Memory Access):** A hardware feature that allows certain devices (disk controllers, network cards, GPUs) to copy data **directly into RAM** without involving the CPU for each byte.

### **Multiprogramming vs Multiprocessing**
- **Multiprogramming:** OS switches between **multiple programs** to keep CPU busy (single CPU).
- **Multiprocessing:** System has **multiple CPUs/cores**.





---
# Chapter 2 -- OS Structure
- Systems calls -- "trap", how system calls differ from interrupts
- OS architecture -- monolith vs layered vs micro-kernel (characteristic features of each, why good/bad)
- Linkers, loaders -- what they are (how they relate to memory management -- cross to Chapter 9)

### **System Calls & Traps**
**Trap:**  
Software-generated interrupt used to enter kernel mode.

**System call vs Interrupt**

| System Call                 | Interrupt               |
| --------------------------- | ----------------------- |
| Intentional by user program | External/hardware event |
| Uses trap instruction       | Comes from device       |
| Synchronous                 | Asynchronous            |

### **OS Architectures**
**Monolithic**
- Very fast (all in kernel)  
    – Hard to maintain/debug

**Layered**
- Clear separation  
    – Hard to design good layers
```
+-------------------------+   ← Layer 5 (User programs)
|    Application Layer    |
+-------------------------+
|    High-Level OS APIs   |   ← Layer 4
+-------------------------+
|   File System, I/O Mgmt |   ← Layer 3
+-------------------------+
| Memory Mgmt, Scheduling |   ← Layer 2
+-------------------------+
| Hardware Interaction    |   ← Layer 1
+-------------------------+
|        Hardware         |   ← Layer 0
```


**Microkernel**
- Minimal kernel → services in user space  
    – Slow due to message passing overhead


### **Linkers & Loaders**
- **Linker:** Combines object files into executable.
- **Loader:** Puts executable into memory and performs **address binding**.






---
# Chapter 3 -- Processes
- Process concept, state, life-cycle, process control block, context switch
- Fork-wait/join paradigm
- Inter-Process Communication (pipes, messaging)


### **Process Basics**
A process = program in execution.

**Process State Cycle:**  
New → Ready → Running → Waiting → Ready → Terminated

**PCB — Process Control Block**  
Contains PID, registers, PC, open files, scheduling info, memory maps.

**Context Switch**  
Saving old PCB + loading new PCB. Overhead, no work done.


### **Fork-Wait/Join**
- **fork():** Creates a child (duplicate process).
- **wait():** Parent waits for child to finish.
- **exec():** Replace process image with another program.


### **IPC: Pipes & Messaging**
- **Pipes:** One-way communication, parent↔child.
- **Message Passing:** send(msg), receive(msg). Useful for distributed systems.





---
# Chapter 4 -- Threads
- Threads, what they are, how they differ from Processes
- Software vs hardware threads,
- POSIX, user-vs-kernel threads (many-to-one, one-to-one, what happens to a process if one of its threads does X)
- Multi-core programming issues, parallelism types


### **What is a Thread?**
A thread is a lightweight unit of execution sharing:
- Code
- Data
- Files

But has its own:
- PC
- Registers
- Stack

**Processes vs Threads**

|Process|Thread|
|---|---|
|Heavyweight|Lightweight|
|Own address space|Share address space|
|Expensive to create|Fast to create|

### **User vs Kernel Threads**
- **User threads:** Mapped by runtime; kernel not aware.
- **Kernel threads:** OS schedules them directly.

**Models**
- Many-to-One (bad: one blocked = all blocked)
- One-to-One (good but expensive)
- Many-to-Many (flexible)


### **Parallelism Types**
- **Data parallelism:** Same operation on different data
- **Task parallelism:** Different tasks on different cores




---
# Chapter 5 -- Scheduling
- CPU Scheduling as a concept, CPU-I/O Burst Cycle
- Scheduler, preemptive vs non-preemptive, when and why scheduler intervenes
- Scheduling criteria (how to measure what's good what's bad and compare schedules)
- Scheduling algorithms (FIFO, SJF, SRTF, Priority, Multi-Level (Feedback) Queue Scheduling)
- Multi-processor scheduling (load balancing, global-vs-local, processor affinity)
- Real-time scheduling (RTS definition (idealistic), soft-vs-hard RTS, Rate Monotonic Scheduling, Earliest Deadline First, Proportional Share Scheduling)


### **CPU Burst / I-O Burst Cycle**
Processes alternate between CPU bursts and I/O waits.

### **Preemptive vs Non-preemptive**
- Preemptive: OS can stop running process.
- Non-preemptive: Process runs until voluntarily yielding.


### **Scheduling Algorithms (core exam topic)**
1. **FCFS** — simple, slow for long jobs
2. **SJF** — optimal for average waiting time, requires prediction
3. **SRTF** — preemptive SJF
4. **Priority** — starvation unless aging
5. **Multilevel Queue** — jobs grouped by type
6. **MLFQ** — dynamically adjusts priority


### **Multi-processor Scheduling**
- **Global queue:** All CPUs share ready queue
- **Local queue:** Each CPU has its own queue
- **Affinity:** Prefer to keep process on same core for cache


### **Real-time Scheduling**
- **Hard RT:** Must meet deadlines
- **Soft RT:** Should meet deadlines
- **Rate Monotonic (RM):** Shorter period → higher priority
- **EDF:** Earliest deadline gets CPU (optimal)




---
# Chapter 6 -- Synchronization Tools
- Critical Section Problem (race condition, basic example, three solution requirements)
- Peterson's solution (flag-and-turn)
- Hardware support for CSP solutions (memory barriers, atomic hardware instructions)
- Mutex, Semaphore (blocking/non-blocking, and implementation issues)


### **Critical Section Problem**
Requirements:
1. Mutual exclusion
2. Progress
3. Bounded waiting

### **Peterson’s Solution**
Uses two arrays:
- `flag[i] = true` (wants to enter)
- `turn = j`

### **Hardware Support**
- Test-and-set
- Compare-and-swap
- Memory barriers

### **Mutex vs Semaphore**
- **Mutex:** Binary lock
- **Semaphore:** Counter; can be blocking or non-blocking





---
# Chapter 7 -- Synchronization Example
- Producer Consumer Examples, Reader-(vs-Writer) priority


### **Producer-Consumer**
- Full/empty semaphores
- Mutual exclusion on buffer

### **Reader-Writer**
- Reader-priority risks writer starvation
- Writer-priority prevents too many readers





---
# Chapter 8 -- Deadlock
- Deadlock definition -- necessary conditions, and why/when they are not sufficient (i.e., do not guarantee deadlock)
- Deadlock Prevention -- methods and their limitations
- Deadlock Avoidance -- Banker's algorithm, you should be able to solve a problem when the data is incomplete (e.g., one of the Available is unknown)
- Deadlock Detection -- Similarity and difference with the Banker's Algorithm, you should be able to solve a problem when the data is incomplete (e.g., one of the Requests is unknown)


### **Four Necessary Conditions**
1. Mutual exclusion
2. Hold-and-wait
3. No preemption
4. Circular wait

All must be true for deadlock to be _possible_.


### **Prevention**
Break at least one of the 4 conditions.


### **Avoidance — Banker's Algorithm**
Know how to compute:
- Need = Max – Allocation
- Available (may be partially unknown on exam)


### **Detection**
Similar to Banker's, but:
- Looks for cycles
- Does _not_ check safe state





---
# Chapter 9 -- Memory Management
- Address binding, linker/loader issues (link from Chapter 2) 
- Basic operation of Segmentation
- Basic operation of Paging
- Structured Paging -- multi-level paging, hashed page tables, inverse page tables


### **Address Binding**
Three stages:
- Compile time
- Load time
- Run time (dynamic relocation)


### **Segmentation**
Logical chunks (code, data, stack) with bounds.


### **Paging**
Divide process into pages, memory into frames.

### **Structured Paging**
- **Multi-level** (page directory → page table)
- **Hashed page tables** (used for big address spaces)
- **Inverted page tables** (one entry per frame)






---
# Chapter 10 Virtual Memory
- What is different between Virtual Memory vs Paging vs Swapping
- Extra "bits" -- valid, dirty, recency bit; and why sometimes we have more bits per concept (e.g., more than 1 recency bit).
- Page replacement algorithms 
	- FIFO, Optimal, LRU, Second Chance, Clock; and remember that there are frequency of use based approaches
	- Page buffering
- Allocation of frames
	- Allocation algorithms (fixed, proportional, reclaiming page, thrashing + working set)
	- Global vs local allocation
- "Speedups" -- page size effects, TLB reach, program structure



### **VM vs Paging vs Swapping**
- **Paging:** Just mapping pages to frames.
- **VM:** Allows program to exceed physical memory using disk.
- **Swapping:** Swap entire processes (older technique).


### **Page Table Bits**
- **Valid:** page present
- **Dirty:** modified
- **Recency (R bit):** last accessed (used for replacement)


### **Page Replacement Algorithms**
1. FIFO
2. Optimal (theoretical)
3. LRU
4. Second Chance
5. Clock
6. Frequency-based (LFU, MFU)


### **Frame Allocation**
- Fixed
- Proportional
- Global vs Local replacement
- Thrashing & Working Set


### **Speedups**
- Larger pages → fewer page faults
- TLB reach → TLB entries × page size
- Good locality improves performance






---
# Chapter 11 -- Mass Storage
- NVMs vs HDDs (how they work, limitations and quirks)
- HDD scheduling (FCFS, SCAN, C-SCAN)
- NVM scheduling (link to Chapter 14 FS Implementation)


### **HDDs vs NVMs**
**HDD:**
- Mechanical
- Slow seeks
- Requires scheduling: FCFS, SCAN, C-SCAN

**NVM (SSD):**
- No seek time
- Wear leveling
- TRIM (clears unused blocks)





---
# Chapter 12 -- Kernel I/O
- Kernel I/O responsibilities (buffering, caching, error handling, protection)  
- I/O Device features 
	- Non-blocking vs Asynchronous I/O
- Memory-mapped I/O -- link-back to Chapter 10
- Interrupts and DMA -- link-back to Chapters 1,2


### **Responsibilities**
- Buffering
- Caching
- Error handling
- Protection

### **Device I/O**
- **Non-blocking:** Returns immediately
- **Async:** Returns later with result

### **Memory-mapped I/O**
Devices mapped into memory address space.






---
# Chapter 13 -- File System Interface
- File and directory concepts, File Control Block
- File Access -- HW vs Logical
- Directory structures
	- Flat, tree, acyclic graph, general graph -- problems and treatments
	- Hard vs soft links


### **Concepts**
- File Control Block (inode)
- Directories as special files

### **Directory Structures**
- Flat
- Tree
- Acyclic Graph (allows sharing)
- General Graph (needs cycle detection)

### **Links**
- **Hard link:** Another directory entry for same inode
- **Soft link:** Points to path





---
# Chapter 14 -- FS Implementation
- FS layered structure
- Kernel (in memory) structures that support FS operations
	- Mount-table, system-wide open files table, per-process open file table
- Directory implementation -- linear (+tree), hash,
- Block allocation methods -- notice the differentiation between management data and file data storage (inodes/FAT use separate disk space)
	- Contiguous
	- Linked (+ extents, FAT)
	- Indexed -- general
		- Unix/Linux (inode)
- Free space management
	- Bitmap (can have several, e.g. one for inodes and one for data blocks)
	- Linked list (+grouping+counting)
- FS Performance Enhancements
	- Buffer-cache
	- Free-behind and read ahead
	- TRIM -- link back to Chapter 11
- Special Lecture -- Chapter 14 (on Recovery and WAFL) + Journaling File Systems (Three Easy Pieces, Chapter 43)
    - FSCK
    - WAFL
    - Journaling and Meta Journaling
- Recommended Reading (no lecture slides): Chapter 15 (File System Internals) of the Operating System Concepts book. 
    - Links together several concepts, discusses mounting in detail, introduces NFS and Virtual File System


### **Layered FS Structure**
App → VFS → FS driver → Block layer → Hardware

### **Key Kernel Structures**
- Mount table
- System-wide open-file table
- Per-process open-file table


### **Directory implementation**
- Linear
- Tree
- Hash


### **Block Allocation**
- Contiguous
- Linked lists (+ FAT)
- Indexed (inodes, extents)


### **Free Space Management**
- Bitmaps
- Linked lists, grouping, counting


### **Performance Enhancements**
- Buffer cache
- Read-ahead, free-behind
- TRIM


# **Journaling / WAFL / FSCK**
- **Journaling:** Write changes to log before committing
- **Meta-journaling:** Only metadata logged
- **FSCK:** Repairs inconsistencies
- **WAFL:** Copy-on-write tree structure, snapshots