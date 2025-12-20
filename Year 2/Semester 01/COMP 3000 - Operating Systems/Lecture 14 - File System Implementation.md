### **Why Disks / NVM Are Used for File Systems**
 **Disks**
- **Rewrite in place** → Can modify a block and write it back to the same location.
- **Random access** → Any block can be accessed directly.

**NVM**
- Cannot rewrite “in place” the same way as disks.
- Still used for file systems, but with different performance characteristics.

**I/O Transfers**
- Done in **blocks** (e.g., 512B or 4KB on disks; 4KB typical on NVM).
- OS transfers whole blocks for efficiency.


### **Two Big File-System Design Problems**
1. **User-level view** (files, attributes, operations, directory structure).
2. **Implementation** (mapping logical view → physical storage using algorithms and data structures).


### **Layered File-System Structure**
**1. I/O Control**
- Device drivers + interrupt handlers.
- Drivers translate high-level ops (“read block 123”) → hardware commands.

**2. Basic File System (“Block I/O Subsystem”)**
- Issues read/write block requests to the driver.
- Works with **logical block addresses**.
- Handles:
    - **Buffer management**
    - **Cache management**
    - **I/O scheduling**

**3. File-Organization Module**
- Understands _files_, _logical blocks_, _free-space management_.

**4. Logical File System**
- Manages **metadata**:
    - FCBs / inodes (ownership, permissions, block pointers)
    - Directory structure
    - Protection
- Resolves file names → file-control blocks.

**Layering pros/cons**
- Pros: Clean, reusable modules.
- Cons: Slight overhead → may reduce performance.


### **File Systems Examples**
- **UNIX** → UFS (Fast File System)
- **Windows** → FAT, FAT32, NTFS
- **Linux** → ext3/ext4 + many others
- **Optical media** → ISO 9660
- **Distributed systems** → remote file systems (network-mounted)
- **FUSE** → allows user-level file-system code.


### **File-System On-Disk Structures**
**Stored on the storage device:**
- **Boot control block**  
    – Contains info to boot an OS from this volume.
- **Volume control block (superblock)**  
    – Total blocks, block size, free blocks, free FCBs.
- **Directory structure**  
    – Names → inode (FCB) mapping.
- **File-Control Block (FCB / inode)**  
    – Metadata: owner, permissions, timestamps, block pointers.


### **In-Memory Structures**
Loaded at mount time, discarded at dismount.
- Mount table
- Directory cache
- System-wide open-file table (one entry per open file)
- Per-process open-file table (file descriptors/handles)
- Buffers / caches for recently used blocks


### **File Operations: Create, Open, Read, Close**
**Create**
1. Logical FS allocates a new FCB.
2. Directory is read → updated → written back.

**Open()**
1. Check **system-wide open-file table**:
    - If already open → just create a per-process entry pointing to it.
2. Otherwise:
    - Search directory for name (often cached).
    - Read FCB into open-file table.
3. Per-process table gets:
    - Pointer to system-wide table
    - Current file offset
    - Access mode

Returns:
- UNIX → file descriptor
- Windows → file handle

**Close()**
- Per-process entry removed.
- System-wide open count decremented.
- When count hits 0 → metadata written back to disk, entry freed.

**Caching**
- Most metadata stays in memory while a file is open.
- Cache hit rates ≈ 85% in UNIX → huge performance gain.


### **Directory Implementation**
**a) Linear List**
Each entry = file name + pointer to metadata.

**Pros**
- Simple to implement.

**Cons**
- **Linear search** → slow for large directories.
- Creating/deleting files requires scanning or shifting entries.
- Many OSes cache directory entries to mitigate slowness.

**b) Hash Table**
Directory =
- Linear list of entries
- Hash table mapping filename → pointer in list

**Pros**
- Much faster lookup than linear list.
- Insert/delete easier.

**Cons**
- Hash table size may need resizing → requires rehashing.
- Collisions need handling (chaining or probing).


### **Allocation Methods**
File systems must decide how to assign blocks to files. Three main methods:

**1. Contiguous Allocation**
**How it works:**
- File = one contiguous sequence of blocks.
- Directory stores: **start block + length**.

**Pros**
- **Fastest** for sequential _and_ direct access (block i = start + i).
- Minimal seeking.

**Cons**
- **External fragmentation** over time.
- Requires knowing file size in advance.
- Growing a file is hard (no space next to it).
- May require expensive compaction (defragmentation).

**Used today?**
- Rare, but concept influences **extents** → allocate chunks that can grow.

**2. Linked Allocation**
**How it works:**
- File = linked list of blocks scattered anywhere.
- Directory stores pointer to **first** and **last** block.
- Each block → pointer to next.

**Pros**
- No external fragmentation.
- File can grow easily.
- No need to predeclare size.

**Cons**
- **Direct access impossible** (must follow pointer chain).
- Pointer overhead.
- Reliability issues (lost pointer breaks file).
- Clustering helps but causes internal fragmentation.

### **FAT = Linked Allocation with table**
- FAT table holds the “next block” pointers for all blocks.
- Allows better random access because FAT is cached.
- Still expensive seeks if FAT not cached.

##**3. Indexed Allocation**
**How it works:**
- Each file has an **index block** containing an array of block pointers.
- Directory stores pointer to the index block.

**Pros**
- **Direct access** supported.
- No external fragmentation.

**Cons**
- Index block overhead (even for tiny files).
- Index block may be too small → need multi-level structures.

### Common solutions:
- **Linked index blocks** (extend index when needed).
- **Multilevel index** (like a page table).
- **UNIX inode scheme**:
    - 12 direct pointers
    - 1 indirect
    - 1 double-indirect
    - 1 triple-indirect  
        → supports huge files efficiently.


#### Performance Comparison

| Method         | Sequential | Direct    | Fragmentation                | Notes                     |
| -------------- | ---------- | --------- | ---------------------------- | ------------------------- |
| **Contiguous** | Excellent  | Excellent | External                     | Must know size; fastest   |
| **Linked**     | Good       | Bad       | None                         | Only sequential efficient |
| **Indexed**    | Good       | Good      | None (except index overhead) | Scales to large files     |


### **Free-Space Management**
Goal: track free blocks efficiently.

**1. Bit Vector**
- 1 = free, 0 = allocated.
- Very fast to find n consecutive free blocks.
- Requires keeping bitmap in memory → can become large.

**2. Linked List**
- Free blocks linked together.
- Simple but slow to traverse.
- Usually used only to pick the _first_ free block.

**3. Grouping**
- Each free block stores addresses of next n free blocks.
- Faster than simple linked list.

**4. Counting**
- Store <start, length> pairs for runs of free blocks.
- Efficient when free space naturally comes in chunks.

**5. Space Maps (ZFS)**
- Device divided into metaslabs.
- Free space tracked using logs + counting.
- Reads log into memory and reconstructs free blocks efficiently.
- Optimized for huge volumes.

**6. TRIM (for SSD/NVM)**
- SSDs must erase blocks before reuse.
- File system uses **TRIM/unmap** to inform device which blocks are free.
- Prevents "write cliff" caused by garbage collection.


### **Recovery & Reliability**
**1. Consistency Checking (fsck)**
- After crash, compare metadata to actual blocks.
- Slow (may take hours).
- May not fix all inconsistencies; can lose files.

**2. Log-Structured / Journaling File Systems**
Used in NTFS, ext3/ext4, ZFS (in different ways).

How it works:
- Metadata updates written first to a **log** (a transaction).
- Only after log entry is committed → real structures updated.
- On crash:
    - Completed transactions replayed.
    - Incomplete ones rolled back.

**Benefits**
- Very fast metadata writes (sequential log writes).
- Much faster crash recovery.

**3. Copy-on-Write (WAFL, ZFS)**
- Never overwrite blocks.
- Writes allocate new blocks; metadata updated atomically.
- Enables:
    - Snapshots
    - Clones
    - Reliable updates without fsck
    - Easy replication


### **WAFL File System (NetApp) — Example**
Optimized for **random writes** and **network file servers**.

**Key concepts:**
1. **Write-anywhere** → never overwrites blocks.
2. **All metadata stored in files**.
3. **Snapshots**:
    - Copy of root inode.
    - Only changed blocks consume extra space.
    - Very cheap to create.
4. **Free-block map** stores not just free/used but which snapshots still reference a block.
5. **Clones** = writable snapshots that share unchanged blocks.
6. **Replication** done by sending changed blocks between snapshots.

WAFL demonstrates how a file system can be tuned for a specific workload (random network writes).
