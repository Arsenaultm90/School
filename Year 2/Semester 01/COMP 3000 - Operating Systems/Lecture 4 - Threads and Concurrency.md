#### Basic Components of a Thread 

A thread is the **smallest unit of execution** within a process. Its components include:
1. **Thread ID**
    - A unique identifier for the thread within its process.
2. **Program Counter (PC)**
    - Keeps track of the next instruction the thread will execute.
3. **Registers**
    - CPU registers storing intermediate data for the thread.
4. **Stack**
    - Each thread has its own stack for local variables and function calls.
5. **Thread State**
    - Current state: running, ready, blocked, etc.
6. **Thread-local storage**
    - Optional per-thread memory for private variables.
7. **Priority (optional)**
    - Determines scheduling order in some OSes.
        

**Shared with other threads in the same process:**
- Code segment
- Global variables
- Heap memory
- Open files and other resources

| Feature               | Process                                            | Thread                                                                      |
| --------------------- | -------------------------------------------------- | --------------------------------------------------------------------------- |
| **Memory**            | Separate address space                             | Shares memory of parent process                                             |
| **Creation overhead** | Heavy-weight                                       | Light-weight                                                                |
| **Communication**     | Inter-process communication (IPC) required         | Can access shared memory directly                                           |
| **Scheduling**        | Scheduled independently                            | Scheduled by the OS as part of the process or individually (kernel threads) |
| **Failure isolation** | One process crashing usually doesn’t affect others | One thread crashing can affect the whole process                            |
| **Use case**          | Running multiple programs                          | Multiple tasks within a program (UI, computation, I/O)                      |
**threads = lightweight sub-processes** that share resources.
**processes = independent execution units with isolated memory**.



---
#### Thread Local Storage

TLS gives _each thread its own copy_ of a variable, even if the variable looks global.
That means:
- Each thread can modify its own value independently.
- No interference, no need for locks.

|Concept|Description|
|---|---|
|**Global variable**|Shared across all threads|
|**Local variable**|Exists only in a function’s stack (private to each thread)|
|**Thread-local variable**|Global in scope, private in value (each thread has its own copy)|

**Why TLS is useful**
- Logging (each thread can keep its own log buffer)
- Random number generators (no shared state)
- Caches (thread-specific data reuse)
- Avoiding synchronization overhead on small, independent state


---
#### Signal Handling

Signals are a form of **software interrupt** used by Unix/Linux systems to notify a process that some event has occurred (e.g., `SIGINT`, `SIGKILL`, `SIGTERM`, etc.).

- Signals are _delivered to the entire process_, not a specific thread.
- The process decides how to handle that signal using **signal handlers** (functions set up with `signal()` or `sigaction()`).

Example :
```
void handler(int signum) {
    printf("Caught signal %d\n", signum);
}

int main() {
    signal(SIGINT, handler); // Catch Ctrl+C
    while(1);
}
```
If you press **Ctrl+C**, the OS sends `SIGINT` to the process, which runs `handler()`.

Threads live _inside_ a process, so:
- All threads **share the same signal handlers** (set by the process).    
- However, **the signal is delivered to one specific thread** — typically:
    - The one that caused the signal (e.g., divides by zero).
    - Or any thread that doesn’t block that signal.

This can get tricky because:
- Threads can **block** or **unblock** certain signals individually (using `pthread_sigmask()`).
- But the **signal handler** is shared by all threads.



---
#### Thread Cancellation

Thread cancellation is when one thread requests another thread to stop executing.

|Type|Meaning|
|---|---|
|**Asynchronous**|Thread stops _immediately_ (unsafe — may corrupt data or leave locks held)|
|**Deferred (default)**|Thread checks for cancellation points (safe)|

A thread can be cancelled with:
```
pthread_cancel(thread_id);
```

The target thread must have cancellation **enabled** and **deferred** (default).  
It will only stop when it reaches a _cancellation point_, such as:
- `pthread_join()`
- `read()`
- `sleep()`
- `printf()`
- `wait()`

This ensures the thread stops safely between system calls.


---
#### Benefits of Multithreaded Applications

- **Responsiveness:**
    - UI threads can remain responsive while background tasks run (e.g., fetching data).
- **Resource sharing:**
    - Threads share memory and resources, making communication easier than between processes.
- **Better CPU utilization:**
    - Multiple threads can run on multiple cores simultaneously.
- **Modularity:**
    - Tasks can be separated into logical units (e.g., I/O thread, computation thread).


---
#### Challenges of Multithreaded Applications

- **Concurrency bugs:**
    - Race conditions: multiple threads accessing shared data simultaneously can cause inconsistent results.
    - Deadlocks: threads waiting on each other indefinitely.
- **Complex debugging:**
    - Thread interleaving is non-deterministic; bugs may be hard to reproduce.
- **Overhead:**
    - Context switching and synchronization mechanisms (mutexes, semaphores) add performance cost.
- **Resource contention:**
    - Threads competing for shared resources can slow performance.


---
#### Implicit Threading

- **Definition:** Threads are created automatically by the system or runtime environment.

- **Example:**
    - **OpenMP:** Compiler automatically splits loops into parallel threads.
    - **Java `parallelStream()`:** Streams execute in parallel without explicit thread management.
        
- **Benefit:** Reduces programmer effort and complexity.
- **Drawback:** Less fine-grained control over scheduling and resources.


**Thread Pools**
- **Definition:** Pre-created group of threads ready to execute tasks.
- **Benefits:**
    - Avoids the cost of creating/destroying threads repeatedly.
    - Efficient for servers handling many short-lived tasks.

- **Example:**
    - Java `ExecutorService`
    - POSIX thread pools

- **Usage pattern:** Submit a task → thread from pool executes → thread returns to pool.


**Fork-Join Parallelism**
- **Definition:** A divide-and-conquer approach:
    1. **Fork:** Split a task into smaller subtasks.
    2. **Join:** Combine the results after all subtasks complete.
- **Benefits:**
    - Natural fit for recursive algorithms (merge sort, quicksort).
    - Efficient use of multicore processors.

- **Example:** Java `ForkJoinPool`


**Grand Central Dispatch (GCD)**
- **Definition:** Apple’s system-level framework for implicit multithreading.
    
- **How it works:**
    - Tasks are submitted to **queues**, not threads.
    - GCD schedules tasks on available system threads automatically.

- **Benefits:**
    - Simplifies concurrency programming on macOS/iOS.
    - Optimizes system resource usage.

- **Example usage:**
```
DispatchQueue.global().async {
    // background work
}
DispatchQueue.main.async {
    // update UI
}
```


---
#### Semantics of fork() and exec()

When a multithreaded process calls `fork()`, does it duplicate only the calling thread or all threads?

**POSIX standard (modern UNIX/Linux/macOS)**
- **Only the calling thread is duplicated** in the child process.
- The other threads **do not exist** in the child — they vanish

So if `Thread 2` calls `fork()`, the new process will contain:
```
Child Process B
 └── Thread 2 (copy)
```

`exec()` usually works as normal – replace the running process  
including all threads


---

**Summary:**

- **Benefits of multithreading:** responsiveness, modularity, parallelism.
- **Challenges:** race conditions, deadlocks, debugging difficulty.
- **Implicit threading:** system handles thread creation.
- **Thread pools:** pre-created threads for repeated tasks.
- **Fork-join:** divide tasks recursively and combine results.
- **GCD:** Apple’s implicit threading for iOS/macOS.