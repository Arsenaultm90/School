#### **General Concepts**

- Operating System (OS) often **guesses future page access**.
- Some applications (e.g., databases) have **better knowledge of access patterns**.
- Memory-intensive applications can lead to **double buffering**:
    - OS keeps a copy of the page as an **I/O buffer**.
    - Application keeps a copy for its own work.
- OS can give **direct access to disk** (raw disk mode):
    - Bypasses buffering, locking, etc.
    - Minimizes interference with application memory usage.


---
#### **Virtual Memory**

- Combines **logical/physical separation** with **sparse use** and **swapping**.
- Goal: make **large memory spaces usable** efficiently.
- Key techniques:
    - **Demand Paging**: MMU schedules disk operations when pages are needed.
    - **Copy-on-Write**: Reduces unnecessary swapping by delaying page copies until modified.
    - **Page Replacement**: Deciding which page to evict when a new page is needed.
    - **Allocation of Frames**: Distributing physical memory among processes.
- Pitfalls:
    - NUMA (Non-Uniform Memory Access) architectures: access speed varies by memory location.


---
#### **Page Replacement Policies**

**Why needed**: when all frames are full and a new page is required.

**Global Replacement**:
    - Process can choose replacement from **any frame**.
    - Pros: higher throughput.
    - Cons: execution time per process may vary.
        
**Local Replacement**:
    - Process chooses replacement from **its own frames**.
    - Pros: more predictable per-process performance.
    - Cons: possible underutilization of memory.


---
#### **Allocation of Frames**

- **Equal Allocation**: divide frames evenly among processes.
    - Example: 100 frames / 5 processes = 20 frames each.
 
- **Proportional Allocation**: allocate according to **process size**.

- **Dynamic Allocation**: adjust allocations as **processes start/finish** or multiprogramming degree changes.

- **Fixed Allocation**: static allocation, does not change during runtime.


---
#### **Reclaiming Pages**

**Goal**: maintain enough free memory to satisfy new requests.

**Strategies**:
    - Maintain a **free-frame list**.
    - **Proactive replacement**: start replacing pages **before free memory is exhausted**.

Page replacement is **triggered based on thresholds**, not only when memory is fully used.


---

#### **Examples & Considerations**

Graphs of **page faults vs. number of frames** show:
    - Each process needs a **minimum number of frames**.
    - Example: IBM 370 requires 6 pages for an SS MOVE instruction (2 pages for instruction, 2 for source, 2 for destination).

Memory-intensive operations and page allocation strategies can significantly **impact performance**.


---
#### **Advanced Considerations**

Some systems use **NUMA (Non-Uniform Memory Access)**:
    - Memory speed depends on **CPU/memory proximity**.
    - Affects **page allocation** and **replacement efficiency**.

Page replacement + allocation strategies need to consider **system architecture** for optimization.


---
#### **1. System Setup**

- **Frames (M)**: physical memory slots available for pages.
- **Reference string (S)**: sequence of page requests.
- **Pages (N)**: distinct pages in the string.
- **Initial state**: usually all frames are empty.

Key rules:
- A **page fault** occurs when a referenced page is **not in memory**.
- If there’s a free frame, the page **loads without replacement**.
- If all frames are full, a **replacement policy** decides which page to evict.
    

---

#### **2. Page Replacement Algorithms**

**a) FIFO (First In First Out)**
Evict the page **loaded earliest** in memory.
    
Easy to simulate with a queue:
    1. Add page to queue if not present (page fault).
    2. If full, remove the **front** page (oldest) and insert the new one.


---

**b) LRU (Least Recently Used)**
- Evict the page that was **used least recently**.

- Track **last access time** for each page.

- Page fault occurs if page not in memory:
    - Insert page if free frame exists.
    - If full, evict **page with oldest last access**.
        

---

**c) Second Chance / CLOCK**
- Like FIFO but gives a **second chance**:
    - Each page has an **R-bit** (reference bit).
    - On replacement:
        1. Look at the next page in FIFO order.
        2. If R-bit = 1, clear it and move to the back of the “clock”.
        3. If R-bit = 0, evict the page.


---

#### **3. How to Calculate Page Faults**

**Step-by-step method**:
1. Start with **empty frames**.
2. Go through the **reference string**:
    - If page already in frame → no fault.
    - If page not in frame → page fault, load page.
    - If memory full → apply **replacement policy** to evict one page.
3. Count **number of times a page fault occurs**.
    

---
#### **4. Bounding Page Faults**

**Given**: FIFO, M frames, S reference string of length L, N distinct pages.
- **N ≤ M** (enough frames for all pages)
    - Lower bound X = N?
        - Each unique page will be loaded **at least once**.
    - Upper bound X = N?
        - Once all N pages are loaded, no more faults.
- **N > M** (not enough frames)
    - Lower bound X = M?
        - At least one page per frame, then reuse may avoid some faults.
    - Upper bound X = L?
        - Worst case: every access is a page not in memory → **all L accesses fault**.
- Changing FIFO → LRU:
    - Some bounds may **improve** (fewer faults if LRU predicts better).


---
#### **Algorithms**

**1. FIFO (First In, First Out)**

**Idea:**
- Replace the page that **has been in memory the longest**.
- Think of a queue: the first page to come in is the first to go out.

**How it works:**
1. Keep track of the **load time** of each page (or use a queue to track order).
2. When a new page must be loaded and memory is full:
    - Evict the page that was loaded **earliest**.
3. Load the new page into that frame.

**Key point:**
- **FIFO uses the order pages were loaded**, NOT their page number or frequency of use.
- So even if the page is heavily used, it could be evicted if it’s the oldest.

**Example:**  
Frames: `[0, 1, 2]` loaded in order 0 → 1 → 2.
- Next page to load: 3
- Evict **0** (first loaded) → new frames: `[3, 1, 2]`.


---

**2. LRU (Least Recently Used)**

**Idea:**
- Replace the page that **hasn’t been used for the longest time**.
- Uses **temporal locality**: pages recently used are more likely to be used again soon.

**How it works:**
1. Track **last access time** for each page.
2. When a new page must be loaded and memory is full:
    - Evict the page with the **oldest last access time**.
3. Load the new page and update its last access time.

**Key point:**
- LRU is smarter than FIFO because it considers **actual usage**, not just arrival order.
- Requires either timestamps or a data structure like a linked list to track usage.


---

**3. Second Chance (FIFO + R-bit)**

**Idea:**
- A modified FIFO to **avoid evicting pages that are being used**.
- Each page has a **reference bit (R-bit)**.

**How it works:**
1. Pages are in a FIFO queue.
2. When a page must be replaced:
    - Check the first page in the queue.
        - **R-bit = 0** → evict it.
        - **R-bit = 1** → reset R-bit to 0, move page to the back of the queue (give a “second chance”).
3. Repeat until a page with R-bit 0 is found.

**Key point:**
- Gives frequently accessed pages a “second chance” before eviction.
- Approximates LRU but is easier to implement efficiently.


| Algorithm     | Replacement criteria       | Notes                                       |
| ------------- | -------------------------- | ------------------------------------------- |
| FIFO          | Oldest loaded page         | Order is by **load time**, not page number  |
| LRU           | Least recently used        | Evicts page unused for the longest time     |
| Second Chance | Oldest page with R-bit = 0 | Gives recently used pages a “second chance” |
