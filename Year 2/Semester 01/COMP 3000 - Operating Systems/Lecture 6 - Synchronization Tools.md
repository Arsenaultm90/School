#### The Critical Section Problem

When **multiple processes (or threads)** execute concurrently and **access shared data or resources**, you can get **race conditions**,  inconsistent results because operations interleave unpredictably.

To avoid that, we define a section of code called the **critical section**, where a process **accesses shared resources** (like variables, files, buffers, etc.).

Only **one process should execute its critical section at a time**.


**The Problem**
We must design a protocol that ensures:
1. **Mutual Exclusion**  
    Only one process can be in its critical section at once.
    
2. **Progress**  
    If no process is in the critical section, one of the waiting processes should be allowed to enter without unnecessary delay.
    
3. **Bounded Waiting**  
    A process waiting to enter its critical section shouldn’t wait forever; there’s a limit to how many times others can go first.


**Context Switching**
A **context switch** happens when the CPU stops executing one process and starts executing another.
- The **“context”** of a process includes everything the CPU needs to resume it later:
    - Program counter (where it left off)
    - CPU registers
    - Stack pointer
    - Process state
- The OS **saves the current process’s context**, picks a new process to run from the **ready queue**, and **loads its context** into the CPU.


---
#### Software Solution : Peterson's Algorithm

Peterson’s solution is a **software-only algorithm** that guarantees mutual exclusion and satisfies all three conditions — **for two processes only**.

Let’s call them **P0** and **P1**.

**Shared Variables :**
```
bool flag[2];     // flag[i] = true means Pi wants to enter CS
int turn;          // whose turn it is to enter
```

**Algorithm :**
```
do {
    flag[i] = true;          // I want to enter
    turn = j;                // Give the other process a chance
    while (flag[j] && turn == j);  // Wait if other wants in and it's their turn

    // ---- CRITICAL SECTION ----

    flag[i] = false;         // Done with critical section

    // ---- REMAINDER SECTION ----
} while (true);
```

- **Mutual Exclusion:** Both can’t be in the CS because one’s `turn` will block the other.
- **Progress:** If no one’s in CS, one can proceed immediately.
- **Bounded Waiting:** `turn` alternates fairly. Each process gets a turn eventually.


---
#### Memory Barrier

A **memory barrier** is a special CPU instruction that **forces memory consistency**.

It ensures:
> All memory operations (loads and stores) before the barrier are completed  
> and visible to all processors **before** any operation after the barrier executes.

So even if the CPU or compiler _tries_ to reorder, the barrier **prevents it**.


**The Issue**
Peterson’s algorithm assumes a **sequentially consistent memory model**, meaning:
> All processes see memory operations (reads/writes) in the exact order they were issued.

That assumption was **true on older CPUs**, but **not on modern ones**.

Modern processors (Intel, AMD, ARM, etc.) and compilers **reorder instructions** for performance and that can **break synchronization algorithms** written purely in software, like Peterson’s.

Both **CPUs** and **compilers** can change the apparent order of operations to optimize execution.
Example:
```
flag[i] = true;
turn = j;
```

The CPU or compiler might **reorder** these, writing `turn = j` _before_ `flag[i] = true`.

In Peterson’s algorithm, this breaks correctness. The other thread might see `turn == j` before it even sees that `flag[i] = true`, leading both processes to think it’s safe to enter their critical sections.

This violates **mutual exclusion**.


**The Solution**
A **memory barrier** (or **fence**) is a low-level instruction that tells the compiler and CPU:
> “Do not reorder memory operations across this point.”

It forces all reads and writes **before** the barrier to complete before any reads/writes **after** it begin.

**Strongly Ordered (Sequential Consistency)**
- Every write to memory by one processor is **immediately visible** to all others.
- The **order of operations** in the program matches the **order seen by all CPUs**.
- Classic CPUs (like early x86) behave mostly this way.
- This is what algorithms like **Peterson’s** assume.

Easy to reason about, but slower (no reordering allowed).

**Weakly Ordered**
- A processor can **reorder** its memory operations (loads/stores) for efficiency.
- Memory writes may not be immediately visible to other processors.
- Common on **modern CPUs** (ARM, RISC-V, PowerPC).

Dangerous for synchronization algorithms that assume everyone sees memory in the same order.



---
#### Hardware Support

Hardware offers **atomic operations**, operations that can’t be interrupted, to simplify synchronization.


 **Test-and-Set Instruction**
Atomically tests and modifies a memory value.

Properties  
	• Executed atomically  
	• Returns the original value of passed parameter  
	• Set the new value of passed parameter to true

```
bool TestAndSet(bool *target) {
    bool rv = *target;
    *target = true;
    return rv;
}
```

Usage:
```
bool lock = false;

do {
    while (TestAndSet(&lock));  // Wait until lock becomes false
    // ---- CRITICAL SECTION ----
    lock = false;               // Release lock
} while (true);
```

**Pros:** Simple, works for multiple processes  
**Cons:** Busy waiting (spinlock)


**Compare-and-Swap (CAS)**
Properties  
	• Executed atomically  
	• Returns the original value of passed parameter value
	
```
int CompareAndSwap(int *value, int expected, int new_value) {
    int temp = *value;
    if (*value == expected)
        *value = new_value;
    return temp;
}
```

Used in lock-free data structures and thread-safe atomic operations.


**Disabling Interrupts**
A very low-level approach — prevent context switches entirely during the critical section.  
Not used in user programs (too dangerous), but used by OS kernels in small sections.


**Atomic Variables**
An **atomic variable** is one where **operations on it happen as a single, uninterruptible step**.
> “Atomic” means **indivisible** - The operation **cannot be interrupted or observed in a partially completed state** by any other thread or process.

**Properties:**
- Prevents race conditions in simple operations (like counters, flags, references)
- Used in **lock-free** and **wait-free** algorithms
- Often built on hardware instructions like:
    - `test-and-set`
    - `compare-and-swap (CAS)`
    - `fetch-and-add`

---
#### Mutex (Mutual Exclusion Lock)

A **binary lock** used to ensure only one thread enters the critical section.

**Operations:**
- `lock()` or `acquire()` — waits if locked, otherwise takes the lock.
- `unlock()` or `release()` — frees the lock.

Example :
```
mutex lock;

do {
    lock.acquire();
    // ---- CRITICAL SECTION ----
    lock.release();
    // ---- REMAINDER SECTION ----
} while (true);
```


---
#### Semaphore

A **more general synchronization tool** introduced by Dijkstra.
	• Semaphore S – integer variable  
	• Can only be accessed via two indivisible (atomic) operations: wait() and signal()  
	• Originally called P() and V()

It’s an integer variable accessed only through **atomic operations**:
	**Types:**
		- **Binary Semaphore:** acts like a mutex (0 or 1)
		- **Counting Semaphore:** counts available resources (e.g., available buffers)
	**Operations:**
- `wait(S)` — also known as `P(S)` or `down(S)` :    
```
// Busy-Wait
wait(S) {  
	while (S <= 0)  
		; // busy wait  
	S--;  
}

// Block w/ Waiting & Queue
typedef struct {  
	int value;  
	struct process *list; // waiting queue  
} semaphore;

wait(semaphore *S) {  
	S->value--;  
	if (S->value < 0) {  
		add this process to S->list;  
		block();  
	}  
}  
```
- `signal(S)` — also known as `V(S)` or `up(S)`:
```
// Busy-Wait
signal(S) {  
	S++;  
}

// Block w/ Waiting & Queue
signal(semaphore *S) {  
	S->value++;  
	if (S->value <= 0) {  
		remove a process P from S->list;  
		wakeup(P);  
	}  
}
```


Example :
```
semaphore mutex = 1;

do {
    wait(mutex);
    // ---- CRITICAL SECTION ----
    signal(mutex);
    // ---- REMAINDER SECTION ----
} while (true);
```

Semaphores can also handle **producer-consumer**, **reader-writer**, and **dining philosophers** problems.


**Two Operations:**
**block (P operation / wait)**
- Purpose: When a process cannot proceed (e.g., resource not available), **it is placed on a waiting queue**.
- Conceptually:
```
block(s):
    place process in s.waiting_queue
    change its state to BLOCKED
```
**Effect:**
- The process **stops running**.
- It won’t consume CPU cycles.
- Will stay blocked **until another process signals** that the resource is available.

**wakeup (V operation / signal)**
- Purpose: **Move a blocked process to the ready queue** when the resource becomes available.
- Conceptually:
```
wakeup(s):
    remove a process from s.waiting_queue
    place it in the ready queue
```
**Effect:**
- The previously blocked process is now eligible to run.
- It will run **based on scheduling policy**.

**How They Work Together:**
Imagine a **counting semaphore** `s` initialized to the number of available resources:
- **Wait / P / block operation:**
    1. Decrement `s`.
    2. If `s < 0`, **no resources are free** → `block()` the process.
    3. If `s ≥ 0`, the process continues → it got a resource.
        
- **Signal / V / wakeup operation:**
    1. Increment `s`.
    2. If `s ≤ 0`, **there are blocked processes waiting** → `wakeup()` one of them.

---
#### Liveness

**Liveness** refers to the property that a system **keeps making progress** — that something _good_ will eventually happen.

> It ensures that processes don’t get stuck forever (no infinite waiting or permanent blocking).

If two processes alternate entering their critical sections, both are _alive_ — they’re both making progress over time.

| Property            | Meaning                                                                             |
| ------------------- | ----------------------------------------------------------------------------------- |
| **Progress**        | If a process wants to enter its critical section, it will eventually be allowed to. |
| **Bounded Waiting** | There’s a limit to how long any process waits to enter its critical section.        |
| **No Starvation**   | Every process eventually gets its turn; no one is ignored forever.                  |

When Liveness Fails:
- Deadlocks (everyone waits forever)
- Starvation (one process never gets access)
- Infinite loops (process never yields)



---
#### Deadlock

A **deadlock** occurs when **two or more processes are waiting indefinitely** for each other to release resources.

> None of them can proceed, because each one is holding something the other needs.

**Example:**
Two threads, two locks:
```
Thread 1:             Thread 2:
lock(A);              lock(B);
lock(B);              lock(A);
```

If both threads lock their first resource at the same time, each will wait forever for the other to release the second.

A deadlock can only occur if **all four** of these are true:

| Condition               | Description                                                                         |
| ----------------------- | ----------------------------------------------------------------------------------- |
| **1. Mutual Exclusion** | At least one resource must be held in a non-sharable mode.                          |
| **2. Hold and Wait**    | A process holding a resource is waiting for others.                                 |
| **3. No Preemption**    | Resources can’t be forcibly taken away.                                             |
| **4. Circular Wait**    | A circular chain of processes exists, each waiting for a resource held by the next. |
If you **break any one** of these, deadlocks can be prevented.


**Ways to Handle Deadlock:**

| Strategy                 | Description                                                                      |
| ------------------------ | -------------------------------------------------------------------------------- |
| **Prevention**           | Design the system to avoid one of the 4 conditions (e.g., lock ordering).        |
| **Avoidance**            | Use algorithms (like **Banker’s Algorithm**) to ensure safe resource allocation. |
| **Detection & Recovery** | Allow deadlocks, then detect and resolve them (e.g., kill one process).          |
