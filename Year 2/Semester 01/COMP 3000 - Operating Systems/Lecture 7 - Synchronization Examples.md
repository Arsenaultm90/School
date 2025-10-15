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
- Correctly **coordinate waiting and signaling** so no process starves.

**Typical Solution Using Semaphores :**
```
semaphore empty = N   // Number of empty slots
semaphore full = 0    // Number of full slots
semaphore mutex = 1   // Mutual exclusion

Producer:
    wait(empty)
    wait(mutex)
    add item to buffer
    signal(mutex)
    signal(full)

Consumer:
    wait(full)
    wait(mutex)
    remove item from buffer
    signal(mutex)
    signal(empty)
```



---
#### **Readers and Writers Problem**



