#### **Main Memory and Multiprogramming**

- **CPU access:** CPU can only directly access **main memory** and **registers**.
- **Memory operations take time**:
    - Register access → 1 CPU cycle (or less)
    - Main memory → several cycles → may **stall the CPU**
    - **Cache** sits in between to reduce latency.

- **Multiprogramming problem:**
    - Multiple programs need to run concurrently.
    - Main memory is limited → loading all programs together is hard.
    - Leads to **fragmentation and protection issues**.


---
#### **Try-1: Load all programs into memory one after another**

- Idea: Allocate memory **contiguously** for each program in a single partition or segment.
    
- **Mechanism:**
    - Each process can only access **its own address space**.
    - **Base and limit registers** define accessible memory:
        - **Base register:** starting physical address of the process
        - **Limit register:** size of the addressable memory
    - **Hardware protection:** CPU checks each memory access against these registers.

- **Problem:**
    - Fixed partitions → wasted space (internal fragmentation)
    - Large programs → cannot fit if memory is fragmented
    - Moving programs requires recompiling (if addresses are absolute)


---
#### **Address Binding**

Binding associates program instructions and data with memory addresses. Can happen at:
1. **Compile-time:**
    - Memory addresses known in advance → absolute code generated
    - Must recompile if program is loaded elsewhere
2. **Load-time:**
    - Memory location not fixed → relocatable code generated
    - Base register added at load-time → program can be loaded anywhere
3. **Execution-time:**
    - Memory location determined at run-time → allows **dynamic relocation**
    - **MMU (Memory Management Unit)** required
    - Logical addresses (used by CPU) → mapped to physical addresses (seen by memory)


---
#### **Memory-Management Unit (MMU)**

- Hardware device that maps **virtual/logical addresses** → **physical addresses**.
    
- Relocation register (a generalization of base register) added to **logical addresses** at run-time.
    
- Benefits:
    - Programs don’t know physical memory → easier to move processes
    - Provides protection: process cannot access addresses outside its range


---
#### **Contiguous Memory Allocation**

- Memory is divided into **blocks or partitions**.
    
- Two common approaches:
    1. **Fixed-sized partitions:** Each partition is fixed in size. Programs are assigned to a partition large enough to hold them.
        - **Problem:** Internal fragmentation (unused space inside a partition).
    2. **Variable-sized partitions:** Partitions are made just large enough for each program.
        - **Problem:** External fragmentation (gaps between partitions accumulate over time).

- **Segments:** logical divisions of a program (code, data, stack). Can be allocated contiguously, but same fragmentation issues occur.


---
#### **Try-2:  Paging**

- **Problem with contiguous allocation:** still too rigid and inefficient.
    
- **Paging solution:**
    - Break memory into **frames** (physical) and programs into **pages** (logical)
    - Pages can be loaded into **any free frame** → **eliminates external fragmentation**
    - **Internal fragmentation** limited to last page

- **Cost:** Requires **page tables** → extra memory overhead and address translation

**Page Table Structure**
Each entry typically contains:
- Frame number (where page is in physical memory)
- Present/absent bit (is page in memory?)
- Protection bits (R/W/X)
- Optional: dirty/modified bit, reference bit

> CPU generates a logical address → MMU looks it up in the page table → physical address accessed


---
#### **What if all programs don’t fit in main memory?**

- **Swapping:** Move processes in/out of memory as needed → CPU can run processes that are not fully in memory
    
- **Virtual memory:** Generalizes swapping:
    - Only **needed pages** are brought into memory
    - Supports programs **larger than physical memory**
    - Enables demand paging and page replacement algorithms


**Key Concepts From Slides**
- **Logical vs Physical addresses:** CPU sees logical, MMU translates to physical
- **Base/relocation registers:** Provide dynamic relocation and protection
- **Memory binding:** Can occur at compile, load, or execution time
- **Main memory + registers = only directly accessible storage**


**Dynamic Allocation Problem:**
First-fit: Allocate the first hole that is big enough  
Best-fit: Allocate the smallest hole that is big enough; must search entire list, unless ordered by size  
	Produces the smallest leftover hole  
Worst-fit: Allocate the largest hole; must also search entire list  
	Produces the largest leftover hole  
Comparing these:  
	First-fit and best-fit better than worst-fit in terms of speed and storage utilization