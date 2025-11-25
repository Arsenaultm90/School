Mass-storage = non-volatile storage used for long-term data.

### **Hard Disk Drives (HDDs)**

Traditional mechanical storage. Key components:
- **Platters** – circular disks coated with magnetic material.
- **Spindle** – rotates platters (e.g., 5400–7200 RPM for consumer HDDs).
- **Read/Write Heads** – one per surface; float above platter.
- **Actuator Arm** – moves heads across the platter.
- **Tracks** – concentric circles on the platter.
- **Sectors** – smallest physical storage unit (usually 512B or 4KB).
- **Cylinders** – all tracks lying under the heads at a given arm position.


**Access Time Breakdown**
Disk access time = **Seek Time + Rotational Latency + Transfer Time**
- **Seek Time** – move actuator arm to correct track. (typical 3–12 ms)
- **Rotational Latency** – wait for sector to rotate under head.  
    Average latency = ½ rotation  
    e.g., 7200 RPM → (1/7200 min per rev) = 8.33 ms full rotation → avg 4.16 ms.
- **Transfer Time** – depends on rotation speed & data size (microseconds range).

**Example:**
```
Access Latency = Average access time = average seek time + average latency  
	• For fastest disk 3ms + 2ms = 5ms  
	• For slow disk 9ms + 5.56ms = 14.56ms  
	• Average I/O time = average access time + (amount to transfer / transfer rate) +  controller overhead  
For example to transfer a 4KB block on a 7200 RPM disk with a 5ms average seek time, 1Gb/sec transfer rate with a .1ms controller overhead.
```

**A) Disk rotates at 7200 revolutions per minute.**
Convert to milliseconds per rotation:
1 rotation = $\frac{1}{7200}​$ minutes  
→ $\frac{1}{7200} \times 60,000$ ms  = 8.33ms per rotation

Average latency = **half a rotation**:
$\text{Avg latency} = \frac{8.33}{2} = 4.17 \text{ ms}$

**B) Compute Transfer Time**
We are transferring **4 KB** across a **1 Gb/s** link.

Convert 4 KB → bits
- 4 KB = 4096 bytes
- 1 byte = 8 bits
- So 4096 × 8 = **32,768 bits**

Convert 1 Gb/s → bits per millisecond
1 Gb/s = 1,000,000,000 bits per second / 1000 = 1,000,000 bits per ms  

**Transfer time:**
$\text{Transfer time} = \frac{32768 \text{ bits}}{1,000,000 \text{ bits/ms}} = 0.032768 \text{ ms}$
≈ **0.033 ms**

**C) Total I/O time= $5+4.17+0.1+0.031=9.301$ ms**
**A 4 KB read takes **~9.3 ms** on a HDD.


**Solid-State Drives (SSD / NVMe)**
- No moving parts → **microsecond** latency.
- Built with **NAND flash memory**.
- Organized in: **Pages → Blocks → Planes → Dies**.
- Access is asymmetric:
    - Reads = fast
    - Writes = slower
    - Erase = slowest (must erase entire block before rewrite)

**Wear-leveling** required since flash blocks degrade with writes.


**Other Storage**
- Non-volatile memory (NVM): NVMe SSDs using PCIe.
- RAID arrays: redundancy & performance improvements using multiple drives.


---
## **HDD Scheduling Algorithms**

Because HDDs have mechanical delays (especially _seek time_), scheduling algorithms reorder requests to minimize head movement.

Assume a disk with tracks 0–199 and current head at track 50  
Pending requests: **82, 170, 43, 140, 24, 16, 190**

##### **2.1 FCFS (First-Come First-Served)**
Simply process requests in order of arrival.

Sequence:  
50 → 82 → 170 → 43 → 140 → 24 → 16 → 190  
Total head movement = large (worst efficiency).

##### **2.2 SSTF (Shortest Seek Time First)**
Pick the request closest to current head.  
This reduces movement but may cause **starvation**.

From 50: nearest is 43 → then 24 → 16 → 82 → 140 → 170 → 190.

##### **2.3 SCAN (Elevator Algorithm)**
Head moves like an elevator: from current position in one direction until end, then reverses.

If moving right:  
50 → 82 → 140 → 170 → 190 → then reverse → 43 → 24 → 16.

Less starvation than SSTF.

##### **2.4 C-SCAN (Circular SCAN)**
One-way elevator: head processes only in one direction.  
When it hits one end, it jumps back to the beginning **without serving requests on the way back**.

50 → 82 → 140 → 170 → 190 → jump to 0 → 16 → 24 → 43  
(Uniform wait times)

##### **2.5 LOOK and C-LOOK**
Variations that **stop early** instead of going all the way to the physical ends.

SCAN vs LOOK = go to end of disk vs go to last request.



---
## **NVM (SSD / NVMe) Scheduling**

SSDs have:
- No seek time
- No rotational latency
- Latency dominated by controller queues & channel parallelism

So HDD algorithms are not used. Instead:

##### **NVMe Queue Structure**
- Supports **multiple submission and completion queues** (up to 64K each).
- Each queue can be assigned to a CPU core → no locking required.
- Eliminates bottleneck of SATA controllers.

##### **Scheduling Goals**
- Maximize **parallelism** across flash channels.
- Balance **read/write** operations (writes are much slower).
- Minimize **erase operations**.

##### **Common Scheduling Techniques**
(Not standard names like HDD scheduling, but concepts.)

**1. Deadline Scheduling**
Prioritize urgent reads/writes to avoid starvation and meet deadlines.

**2. Read Priority**
Reads prioritized over writes (important because:
- Writes cause stalls
- Reads are latency-sensitive for applications)

**3. Wear-Leveling Scheduling**
Distribute writes evenly to increase SSD lifetime.

**4. Garbage-Collection Scheduling**
Flash blocks must be erased before rewriting → costly.  
OS & SSD firmware try to schedule garbage collection during idle periods.


---
## **Error Detection and Correction (EDC/ECC)**

Storage is vulnerable to:
- Bit flips (cosmic rays)
- Stuck bits
- Magnetic decay (HDD)
- Charge leakage (SSD)

##### **Parity Bits**
Simple, low-cost error detection.
- **Even parity**: number of 1s should be even.
- Detects _single-bit errors_, but **cannot fix**.

##### **Checksum**
Used for blocks of data.  
Detects multi-bit errors but still **not correctable**.

##### **CRC (Cyclic Redundancy Check)**
Used in disks and networking.
- Strong error detection.
- Still _not_ used for correction.

##### **ECC (Error-Correcting Codes)**
Used in RAM, SSDs, RAID, and HDDs.

##### **Hamming Codes**
- Corrects 1-bit errors, detects 2-bit errors.

Example:  
Data: 4 bits → add 3 parity bits → 7-bit Hamming code.

##### **BCH/LDPC (modern SSDs)**
- Correct multiple errors per block.
- Essential for NAND flash reliability.


---
## **Storage Space Management**

##### **Low-Level Formatting (Physical Formatting)**
**Purpose:**  
Prepare a physical disk so the **disk controller** knows where sectors are and can read/write them reliably.

**What physical formatting includes:**
When a manufacturer or controller performs low-level formatting, it writes the following onto each sector:
- **Sector header**  
    Contains sector ID, platter/track info, sync bytes.
- **Data area**  
    The actual user-accessible data (commonly **512 bytes**, sometimes 4 KB).
- **ECC (Error Correction Code)**  
    Used by hardware to detect and correct bit-level corruption.

**Why low-level formatting is needed:**
- Defines where each sector physically starts and ends
- Allows controller to _verify_ and _correct_ errors
- Prepares disk before any OS-level file system can be created

**Note:**
Users don’t usually perform physical formatting — it's done by the manufacturer.


##### **Logical Formatting (“Making a File System”)**
Once the physical structure exists, the **OS must write its own metadata** so files can be stored.

This process creates:
- Superblock (file system metadata)
- Free-space maps or bitmaps
- Inode tables (UNIX-like systems)
- Root directory
- Journal (for journaling file systems like ext4, NTFS)

This happens during commands like:  
`mkfs`, `mkfs.ext4`, `format` in Windows.


##### **Blocks vs Clusters**
**Blocks**
- Smallest unit of disk I/O **handled by the OS**.
- Often **4 KB**.

**Clusters**
- A group of blocks treated as the smallest unit for **file I/O**.
- Used to reduce fragmentation and overhead.

**Important distinction:**
- **Disk I/O happens in blocks** (hardware granularity)
- **File I/O happens in clusters** (file system granularity)

**Example:**  
If block = 4 KB and cluster = 8 KB, then:
- Reading 1 cluster = reading 2 blocks.


##### **Partitioning the Disk**
**Why partition a disk?**
Partitioning breaks the disk into one or more **logical disks**, each of which can contain its own file system.

**Partition = a group of contiguous cylinders (HDD) or logical block ranges (SSD).**

**Types of partitions:**
- **Root partition**  
    Contains the OS kernel and core file system. Mounted at boot time.
- **Home/Data partitions**  
    User files, apps, etc.
- **Swap partition**  
    Used for virtual memory.
- **Additional OS partitions**  
    For multi-boot systems.


##### **Mounting File Systems**
To access a file system, the OS must **mount** it.

**Mounting steps:**
1. OS reads the **superblock** of the partition.
2. Runs **file system consistency check (fsck)**
    - Checks metadata: inodes, directory structure, journals, free-block maps.
    - If inconsistent: tries to repair, then retries mounting.
3. If everything is correct, OS adds it to the **mount table**.
4. File system becomes accessible under a directory (e.g., `/mnt/usb`).

**Automatic vs Manual Mount**
- **Automatic**: Root partition, system partitions, entries in `/etc/fstab`.
- **Manual**: Removable drives or user-mounted file systems.


##### **Boot Block and Boot Loader**
Every bootable partition contains a **boot block** (also called MBR on old systems, GPT with EFI on modern systems).

**Boot process overview:**
1. **Bootstrap program in ROM/firmware** runs at power-on.
    - BIOS or UEFI.

2. Firmware loads the **bootstrap loader** from the boot block:
    - MBR (Master Boot Record)
    - EFI System Partition in modern systems

3. Boot loader reads enough of the file system to load:
    - Kernel (`vmlinuz`, `ntoskrnl.exe`)
    - Initramfs or essential startup programs

**Advanced boot managers:**
- GRUB
- Windows Boot Manager
- rEFInd  
    Used for multi-OS booting.


##### **Raw Disk Access**
Sometimes applications bypass the OS’s file-system layer and access disk blocks directly.

**Used by:**
- Database systems (Oracle, MySQL, PostgreSQL)
- High-performance applications
- Real-time applications

**Why?**
- They want **full control over block management**.
- Remove overhead of file-system buffering and metadata.

Example: A database may implement its own buffer cache and free-space manager.


##### **Handling Bad Blocks**
**Bad blocks** = physical locations on disk that cannot reliably store data.

**HDD solution: Sector Sparing**
- When a sector fails, controller remaps it to a “spare sector.”
- Transparency: OS doesn't see the bad block.

**SSD solution: Wear leveling + spare blocks**
- Blocks that degrade are retired.
- Data moved to healthier blocks automatically.


##### **Swap-Space Management**
Swap space supplements RAM by storing pages evicted from memory.

**Purposes:**
- Extend virtual memory
- Allow more processes to run
- Back pages during copy-on-write

**Where swap can be:**
1. **Dedicated swap partition** (fastest)
2. **Swap file** inside a file system (flexible)

**OS performs:**
- Page swapping
- Swap allocation algorithms
- Tracking free swap pages

**Linux swap data structures:**
- Swap map
- Swap slots
- Swap cache (pages being swapped in/out)

**Multiple swap spaces:**
- Can reduce I/O load
- Used to spread paging across different disks
- Improves throughput

**Swap is slow:**
- DRAM: nanoseconds
- SSD: tens of microseconds
- HDD: milliseconds

Therefore excessive swapping → **thrashing**.


##### **Performance Optimization for Secondary Storage**
Since storage is slow compared to RAM, OS tries to optimize:

**Methods:**
- Caching (buffer cache)
- Read-ahead (prefetching entire clusters)
- Write-behind (delayed write)
- Disk scheduling (e.g., SCAN)
- Log-structured file systems
- Journaling for crash recovery


