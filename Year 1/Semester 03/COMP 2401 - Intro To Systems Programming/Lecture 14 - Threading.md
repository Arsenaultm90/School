
Threads represent individual control flows within a process, enabling parallel execution of tasks. Unlike full processes, threads share the same memory space (code, data, and heap segments), making them lightweight and efficient for concurrent operations. However, each thread maintains its own call stack and thread context (Thread ID, program counter, and registers), ensuring independent execution paths. In Linux, threads are implemented as "process groups," but conceptually, they remain parts of a single process.

---
#### **Threading Basics**

To work with threads in C:
1. **Define a function** that the thread will execute.
2. **Create threads** using `pthread_create()`, passing the function and arguments.
3. **Wait for completion** with `pthread_join()` to synchronize thread execution.
4. **Compile** with the `-lpthread` flag (e.g., `gcc -o program program.c -lpthread`).

Threads share:
- Global and heap variables.
- The virtual address space of the process.

However, each thread’s stack is private, though accessible via pointers if shared deliberately.

---
#### **Concurrency Challenges**

When threads access shared data, **race conditions** can occur if operations are not atomic. For example, `count++` (a non-atomic operation) might be interrupted mid-execution, leading to incorrect results. This happens because:

1. Threads read/modify/write data in overlapping sequences.
2. The OS scheduler may switch threads during these operations.

**Example:**
- Two threads increment `count` simultaneously. Without synchronization, the final value might be less than expected due to overlapping updates.
    

---
#### **Synchronization Tools**

To prevent race conditions, synchronization mechanisms like **semaphores** and **mutexes** are used:

1. **Semaphores**:
    - Integer-like counters with atomic `wait()` (lock) and `post()` (unlock) operations.
    - `wait()` decrements the semaphore; if it’s zero, the thread blocks.
    - `post()` increments the semaphore, allowing waiting threads to proceed.

2. **Mutexes** (Binary Semaphores):
    - Restrict access to shared resources by allowing only one thread to hold the lock at a time.
    - Ensure mutual exclusion (`mut-ex`), simplifying critical section management.

**Best Practices**:
- Use synchronization sparingly to avoid performance bottlenecks.
- Always protect shared mutable data.

---
#### **Deadlocks**

Synchronization introduces risks like **deadlocks**, where threads wait indefinitely for locked resources. A classic example:
- **Scenario**: Thread1 locks Resource A and waits for Resource B, while Thread2 locks Resource B and waits for Resource A.
- **Solution**: Enforce a global order for acquiring locks (e.g., alphabetical) to prevent circular dependencies.
    

---
#### **Key Takeaways**

1. **Threads vs. Processes**:
    - Threads are lightweight, share memory, and enable parallel execution within a process.
    - Processes are independent, with separate memory spaces.
        
2. **Concurrency Issues**:
    - Race conditions arise from unsynchronized access to shared data.
    - Atomic operations and synchronization tools (semaphores/mutexes) mitigate these risks.
        
3. **Synchronization**:
    - Semaphores generalize locking; mutexes are binary locks.
    - Overuse can slow performance; use judiciously.
        
4. **Deadlocks**:
    - Avoid by ordering lock acquisitions and ensuring timely releases.
        

---
#### **Study Focus**

- Understand thread creation/management in C (`pthread` functions).
- Recognize scenarios requiring synchronization.
- Differentiate between race conditions and deadlocks.
- Apply mutexes/semaphores to protect shared data in code examples.