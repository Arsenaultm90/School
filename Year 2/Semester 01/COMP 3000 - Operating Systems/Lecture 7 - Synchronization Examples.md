
#### Semaphore
A semaphore is a protected integer variable accessed only through two atomic operations, `wait` and `signal`.  
It is used to control access to shared resources or to synchronize the execution order of threads.  
When a thread calls `wait` and the semaphore value is negative, the thread is blocked and placed into a queue until another thread performs `signal`.

#### **Bounded-Buffer Problem (Producer-Consumer Problem)**

##### Scenario
- There is a **fixed-size buffer** shared between **producers** and **consumers**.
- **Producers** generate data and put it in the buffer.
- **Consumers** take data from the buffer.
- The buffer has **limited capacity**, so:
    - Producers must **wait** if the buffer is full.
    - Consumers must **wait** if the buffer is empty.

##### Key Synchronization Issues
- Avoid **race conditions** when multiple producers/consumers access the buffer.
- Ensure **mutual exclusion** when accessing the buffer.
- Correctly **coordinate waiting and signalling** so no process starves.

**Typical Solution Using Semaphores :**
```
semaphore empty = N   // Number of empty slots
semaphore full = 0    // Number of full slots
semaphore mutex = 1   // Mutual exclusion, Binary lock

Producer:
	produce_item()
	
    wait(empty) // Wait until buffer has empty slot
    wait(mutex) // Lock critical section
    
    insert_item() // Add item to buffer
    
    signal(mutex) // Unlock critical section
    signal(full) // Inrease count of full slots

Consumer:
    wait(full) // Wait until buffer has a filled slot
    wait(mutex) // Lock critical section
    
    remove_item() // Remove item from buffer
    
    signal(mutex) // Unlock critical section
    signal(empty) //Increase empty slots
    
    consume_item()
```



---
#### **Readers and Writers Problem**

- Multiple **readers** can read the shared data _simultaneously_.
- **Writers** need _exclusive_ access.

**Reader Priority version**
Readers should **not wait unless a writer is currently writing**.
This can cause **writer starvation** (important exam point!).

**Semaphores:**

| Name        | Type    | Purpose                              |
| ----------- | ------- | ------------------------------------ |
| `mutex`     | binary  | Protects `readcount`                 |
| `rw_mutex`  | binary  | Controls access to the _shared data_ |
| `readcount` | integer | Number of active readers             |
|             |         |                                      |
#### Reader Priority:
**Reader Pseudocode:**
```
// protects readcount (so only one thread updates it at a time)
semaphore mutex = 1;      

// controls access to the shared resource (DB, file, etc.)
semaphore rw_mutex = 1;   

// number of active readers
int readcount = 0;       


wait(mutex);        // Only one reader at a time can change readcount.
readcount++;    // If this is the first reader, it must block writers.

// If first reader, lock rw_mutex to prevent access to writers
if (readcount == 1)
    wait(rw_mutex);    

// release mutex so other readers can update readcount too.
signal(mutex); 

// Multiple readers can be here at the same time,
// because only rw_mutex protects the shared resource,
// and it is held collectively by all readers together.
read_data();           

// lock access to readcount again to update it safely.
wait(mutex);

// this reader is leaving.
readcount--;

// If last reader, unlock rw_mutex to allow writers
if (readcount == 0)
    signal(rw_mutex);

// Release mutex so other readers can update readcount.
// After this, another reader may enter or leave.
signal(mutex);
```


**Writer Pseudocode:**
```
wait(rw_mutex);    // Exclusive access
write_data();
signal(rw_mutex);
```


#### Writer Priority:
Writer-priority means no new reader can start once a writer is waiting.  
The first writer locks `write_mutex`, blocking ALL new readers, while existing readers finish normally.  
Only after ALL writers finish do new readers proceed.
Reader Code:
```
wait(write_mutex);         // 1) block if writers are waiting or writing
wait(mutex);               // 2) enter readcount modification
readcount++;
if (readcount == 1)
    wait(rw_mutex);        // 3) first reader blocks writers from writing
signal(mutex);
signal(write_mutex);       // 4) allow next reader ONLY if no writer is waiting

// ----- CRITICAL SECTION (READING) -----
read_data();

wait(mutex);
readcount--;
if (readcount == 0)
    signal(rw_mutex);      // last reader releases writers
signal(mutex);
```

Writer Code:
```
wait(mutex);
writecount++;               // writer is now waiting
if (writecount == 1)
    wait(write_mutex);      // first waiting writer blocks new readers
signal(mutex);

wait(rw_mutex);             // exclusive access to data

// ----- CRITICAL SECTION (WRITING) -----
write_data();

signal(rw_mutex);

wait(mutex);
writecount--;
if (writecount == 0)
    signal(write_mutex);    // no more writers waiting → let readers in
signal(mutex);
```
