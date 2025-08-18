#### Threads 

**Introduction :**
- A **thread** is the smallest unit of execution within a process.
- Multiple threads within a process share memory, file descriptors, and other resources.
- Using threads allows a program to do multiple things simultaneously (e.g., downloading a file while updating a progress bar).

**Summary :**
- Threads are created using the POSIX threads (`pthread`) library in C.
- Threads share the same address space, so they can easily communicate—but this also makes synchronization **critical**.
- Each thread runs a specific function concurrently with others.

|Function|Description|
|---|---|
|`pthread_create()`|Creates a new thread|
|`pthread_join()`|Waits for a thread to finish|
|`pthread_exit()`|Ends the calling thread|
|`pthread_t`|The thread type (a handle)|



---
#### Semaphores

**Introduction :**
- A **semaphore** is a synchronization primitive used to control access to a shared resource.
- It’s used to prevent **race conditions** by ensuring only one thread (or a limited number) accesses a resource at a time.

**Summary :**
- `sem_t` is a POSIX semaphore type.
- Think of a semaphore as a counter:
    - `sem_wait()` decrements the counter and may block if the counter is 0.
    - `sem_post()` increments the counter, potentially unblocking other threads.
- Used in **critical sections** to avoid data corruption.

|Function|Description|
|---|---|
|`sem_init()`|Initializes a semaphore|
|`sem_wait()`|Waits (decrements) the semaphore|
|`sem_post()`|Signals (increments) the semaphore|
|`sem_destroy()`|Destroys the semaphore|

Example :
When a thread **wants access to a shared resource**, it uses `sem_wait(&semaphore)`.

If the semaphore is **available (non-zero)**:
- The thread **decreases** its value (decrements it by 1).
- It **continues execution** — it now "owns" the lock.

If the semaphore is **unavailable (zero)**:
- The thread is **blocked**.
- It will **wait (pause execution)** until another thread **unlocks** it using `sem_post(&semaphore)`.

```
int shared_data = 0;
sem_t lock;

void *thread_func(void *arg) {
    sem_wait(&lock);   // Try to lock access
    shared_data++;     // Safely modify shared resource
    sem_post(&lock);   // Unlock access
    return NULL;
}
```
