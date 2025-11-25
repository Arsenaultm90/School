# **CHAPTER 7 — Synchronization**

## **Producer–Consumer Problem**
- Shared buffer between a producer and a consumer.
- Must ensure:
    - Producer cannot insert when buffer is full.
    - Consumer cannot remove when buffer is empty.
- Typically uses:
    - **Semaphore `empty`** = # empty slots
    - **Semaphore `full`** = # full slots
    - **Mutex** = protects access to buffer

### **Solved Example**

**Buffer size = 5**  
Initial: `empty = 5`, `full = 0`, `mutex = 1`.  
Producer executes: `wait(empty)`, `wait(mutex)`, add item, `signal(mutex)`, `signal(full)`.

**Q:** After the producer runs twice and consumer runs once, what are the semaphore values?
- After two producer operations:  
    `empty = 5 − 2 = 3`  
    `full = 0 + 2 = 2`
    
- After one consumer operation:  
    `empty = 3 + 1 = 4`  
    `full = 2 − 1 = 1`
    

**Answer:** `empty = 4`, `full = 1`.

### **Practice Problems**
1. Buffer size = 10. Producer runs 7 times, consumer runs 3 times. Find semaphore values.
	`Semaphore empty = 6`
	`Semaphore full = 4`
2. Show how a race condition occurs if the mutex is removed.
	Two producers executing at nearly identical times. If we increment a variable but haven't stored it yet and then the other producer increments, we will have inserted two items into the buffer but only incremented once.
3. Modify the algorithm so that the producer **waits if full**, but the consumer **has priority** when both want the mutex.
Producer:
```
wait(empty);       // need an empty slot
wait(c_prio);      // consumer must allow producer to run
wait(mutex);

    produce_item();

signal(mutex);
signal(full);      // produced one full slot
```

Consumer:
```
wait(full);        // can only consume full slots
wait(mutex);

    consume_item();

signal(mutex);
signal(empty);     // freed one empty slot
signal(c_prio);    // allow ONE producer to run
```



---
## **Readers–Writers (Reader Priority)**

Goal:
- Multiple readers can read simultaneously.
- Writers need exclusive access.
- With **reader priority**, a writer may starve.

Key variables
- `mutex` protects readCount
- `rw_mutex` protects shared data
- `readCount` tracks active readers

### **Solved Example**
`readCount = 0` initially.

Sequence:
1. Reader1 enters → readCount = 1 → locks `rw_mutex`.
2. Reader2 enters → readCount = 2.
3. Writer arrives → must wait.
4. Reader1 leaves → readCount = 1.
5. Reader2 leaves → readCount = 0 → releases `rw_mutex`.
6. Writer enters.


```
wait(mutex);          // protect readcount
readcount++;
if (readcount == 1)
    wait(rw_mutex);   // first reader locks writers out
signal(mutex);

// CRITICAL SECTION (READING)

wait(mutex);
readcount--;
if (readcount == 0)
    signal(rw_mutex); // last reader releases writers
signal(mutex);
```


```
wait(rw_mutex);

// CRITICAL SECTION (WRITING)

signal(rw_mutex);
```


Question: **Does writer starve?**  
If more readers keep arriving before the last reader leaves, yes—writer may never run.

### **Practice Problems**
1. Write the pseudocode for writer-priority readers–writers.
2. Explain a scenario where writer starvation occurs under reader priority.
3. Add a semaphore that prevents new readers from entering if a writer is waiting.

---
# **CHAPTER 8 — Deadlocks**

## **Deadlock Definition**

Deadlock occurs when a set of processes are permanently waiting for events that only other processes in the set can cause.

### **Necessary Conditions**

(All four must hold.)
1. **Mutual Exclusion**
2. **Hold and Wait**
3. **No Preemption**
4. **Circular Wait**

### **Why Necessary ≠ Sufficient**
Just because all four conditions exist does **not** mean deadlock **will** happen—only that it **can**.

---
## **Deadlock Prevention**

Break one of the 4 conditions:
- **Mutual Exclusion:** make resources sharable (not always possible)
- **Hold and Wait:** require all resources requested at once
- **No Preemption:** allow OS to forcibly take resources
- **Circular Wait:** enforce resource ordering

### **Limitations**
- Often slows system
- Might require processes to request more resources than needed
- Not always possible for physical devices

### **Practice Problems**
1. Show how using resource ordering breaks circular wait.
2. Give an example where hold-and-wait prevention causes starvation.


---
## **Deadlock Avoidance — Banker’s Algorithm**

### **Goal**

Ensure the system never enters an unsafe state.

### **Key Data**
- **Available**: resources free
- **Max**: maximum claim
- **Allocation**: currently allocated
- **Need = Max − Allocation**
    

---
### **Solved Example (with an unknown!)**

Resources: **R1 has 10 units**
```
Allocation     Max       Need
P0  3          7         4
P1  x          5         5-x
P2  3          9         6
Available = ?
```

We know:
`Allocated = 3 + x + 3 = 6 + x`  

So:
`Available = 10 − (6 + x) = 4 − x`

**Find a value of x for which the state is safe.**

Try x = 1:  
Available = 3.

Need array becomes:
- P0 needs 4 → cannot run (3 < 4)
- P1 needs 5−1 = 4 → cannot run
- P2 needs 6 → cannot run

x = 1 → **unsafe**.

Try x = 0:  
Available = 4.

Now:
- P0 needs 4 → can run.  
    Free 3 → Available = 7
- P1 needs 5 → can run
- P2 needs 6 → can run

x = 0 → **safe**.

**Answer:** x = 0 is safe, x = 1 is not.

### **Practice Problems**
1. Solve a banker’s table where one Max entry is unknown.
2. Determine whether the sequence (P1,P3,P0,P2) is safe given a resource table.
3. For a system with 4 resource types, find all values of Available[2] that keep system safe.
    

---
## **Deadlock Detection**

Similar to Banker's but:
- Uses **Requests** instead of Need.
- Checks if all requests can be satisfied with current Available.
- Detection happens **after** deadlock may already exist.

### **Solved Example**

Requests:
```
Allocation Request Available
P0  2        1      1
P1  3        2      1
P2  2        0      1
```

Check:
- P0: needs 1 ≤ Available(1) → ok → Available = 1+2 = 3
- P2: needs 0 ≤ 3 → ok → Available = 3+2 = 5
- P1: needs 2 ≤ 5 → ok

No deadlock.

### **Practice Problems**
1. Find which processes are deadlocked if Request[i] > Available for all i.
2. Given an unknown request value for P3, determine all values that cause deadlock.

---
# **CHAPTER 9 — Memory Management**

## **Segmentation**
- Memory divided into logical segments: code, stack, heap, etc.
- Each has a **base** and **limit** register.
- Logical address → `(segment, offset)`

**Example**  
Segment 2: base=4000, limit=500  
Logical address: (2, 300) → Physical = 4300

### **Practice Problems**
1. Given 5 segments, compute their physical addresses.
2. Check if the address (3, 900) causes a fault given limit=850.

---

## **Paging**
- Memory divided into fixed-size **frames**.
- Logical memory divided into fixed-size **pages** of same size.
- Page table maps page → frame.

### **Example**
Page size = 1 KB  
Logical address = 2500  
Page # = 2500 / 1024 = 2  
Offset = 452  
If page 2 → frame 7 → physical = 7*1024 + 452

### **Practice Problems**
1. Page size = 256 B, logical = 1023. Find physical address.
2. Given a page table, find the physical address or page fault.

---
## **Structured Paging**

### **Multilevel paging**
Break page table into levels (e.g., 2-level or 3-level) to save memory.

### **Hashed page tables**
For big address spaces. Hash page number into a linked list of entries.

### **Inverted page table**
One entry per **physical** frame instead of per linear page.

### **Practice Problems**
1. Compute memory saved by using a 2-level page table.
2. Draw hash chains for given pages.

---
# **CHAPTER 10 — Virtual Memory**

## **Virtual Memory vs Paging vs Swapping**
- **Paging:** divides memory into pages/frames but assumes everything is in RAM.
- **Swapping:** whole processes moved in/out of disk.
- **Virtual Memory:** uses paging + swapping only the needed pages on demand.
    

---
## **Page Table Bits**
- **Valid bit** — page is in memory or not
- **Dirty bit** — page has been modified
- **Reference/Recency bits** — track how recently a page was used (0–1 or multiple bits)

---
## **Page Replacement Algorithms**

### **FIFO**
Remove oldest loaded page.

### **LRU**
Remove least recently used page.

### **Second Chance**
FIFO but give a page a “second chance” if its reference bit = 1.

### **Clock**
Circular list version of Second Chance.

### **Example**
Given pages: **7, 0, 1, 2, 0, 3, 0, 4**  
Frames: 3  
Ask: # faults under FIFO, LRU, Clock.

(I can solve this if you want.)

### **Practice Problems**
1. Compute page faults for FIFO with 4 frames and 10 pages.
2. Compare LRU and Second Chance for a reference string.