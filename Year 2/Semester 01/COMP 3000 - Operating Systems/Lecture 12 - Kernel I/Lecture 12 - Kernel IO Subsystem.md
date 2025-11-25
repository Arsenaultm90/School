## Application I/O Interface

Applications do **not** access hardware directly.  
Instead, they use **high-level interfaces** provided by the OS.

**Common interfaces:**
- **File API:**  
    `open()`, `read()`, `write()`, `close()`
- **Memory-mapped I/O:**  
    `mmap()`
- **Network sockets:**  
    `socket()`, `send()`, `recv()`
- **Non-blocking or asynchronous interfaces:**  
    `select()`, `poll()`, `epoll()`

##### Why abstract hardware?
- Different devices behave differently (disk vs keyboard vs NIC)
- OS provides **uniformity** and hides details
- Ensures **security** (user apps cannot directly modify hardware registers)
- Allows **buffering, caching, scheduling** for performance


---
## Kernel I/O Subsystem

The kernel is responsible for _implementing_ all I/O and hiding hardware details.

**Major responsibilities:**
1. **I/O Scheduling**
Reorder or merge I/O requests to reduce latency  
(ex: SCAN for HDDs, deadline scheduling for SSDs).

2. **Buffering**
Temporarily hold data:
- For smoothing speed mismatch (keyboard vs CPU)
- For network packet reassembly
- For file block caching

3. **Caching**
Keep data in memory to avoid repeated slow I/O:
- File system cache / buffer cache
- Page cache
- Network socket buffers

4. **Spooling**
Queue output for a device that can’t accept interleaved data:  
e.g., print spoolers.

 5. **Device Reservation**
For devices that can’t be shared safely:
- Tape drives
- Scanners
- GPUs (in some cases)

6. **Error Handling**
Kernel handles:
- Retries on read/write failure
- ECC verification
- Reporting I/O errors to applications
- Sector remapping (SSD/HDD controller cooperation)

7. **Device Drivers**
Interface between kernel and hardware controller.

Drivers provide:
- Interrupt handling
- Direct register access
- DMA setup
- Translating OS I/O to hardware commands

This is why Linux has `/dev/sda`, `/dev/ttyS0`, `/dev/fb0`, etc.


---
## Transforming I/O Requests to Hardware Operations

This describes the actual path an I/O request travels.
Example: Application calls `read(fd, buf, 4096)`.

Step-by-step sequence:

**Application → System Call**
Application trapped into kernel mode.

**Kernel checks file descriptor**
Figures out which driver/device this FD is bound to.

**Kernel consults file system or device driver**
If it’s a file:
- File system determines **block number**
- Checks if data is in the **page cache**
- If not, schedules a block I/O

If it’s a device:
- Driver translates call into device-specific commands

**Kernel schedules I/O**
Uses:
- Block scheduler
- Priorities
- Merging adjacent requests (I/O coalescing)

**Hardware operation**
Driver programs the hardware:
- Write device control registers
- Set up DMA
- Issue commands

**Interrupt or Polling**
When device completes:
- It raises an **interrupt**, OR
- Kernel checks via polling (usually slower)

**Data copied into app buffer**
If needed, kernel copies from kernel space to user space.


---
## Performance — Kernel I/O Subsystems

This section is all about _minimizing overhead_ and _maximizing throughput_ when performing I/O.

1. **Reduce Number of Context Switches**
A **context switch** occurs when the CPU switches from one process to another (saving registers, loading new ones).

They are **expensive** (~1–2 µs), so the OS tries to avoid unnecessary ones during I/O.

Examples:
- A process performing synchronous I/O sleeps → causes context switch.
- Using **asynchronous I/O** (AIO) allows process to continue working → fewer switches.
- Network stacks use techniques like **NAPI (New API)** in Linux:  
    switches from interrupt-driven to polling mode under high load to avoid switching too often.

 Fewer switches = lower overhead + higher throughput.


2. **Reduce Data Copying**
Copying data between buffers costs CPU time and memory bandwidth.

Traditional I/O path (slow):
User buffer → Kernel buffer → Device buffer (via driver) → Disk

Optimization: **Zero-copy I/O**
Avoids intermediate copying.

Examples:
- `sendfile()` sends data from disk → network without user-space copy.
- `mmap()` lets user process access file pages directly.
- DMA (below) eliminates CPU copying for large data.

Less copying = less CPU usage + faster I/O.


3. **Reduce Interrupts**
Interrupts trigger context switches, kernel entry, and handler execution.  
Too many interrupts → CPU gets overwhelmed (“interrupt storm”).

Ways the OS reduces interrupts:
**A. Large transfers**

Fewer interrupts if each transfer moves more data.

Example:  
Instead of 4 KB at a time → move 64 KB per interrupt.

**B. Smart controllers**
Modern NICs/HDD/SSDs can:
- Coalesce interrupts (fire one interrupt for many packets)
- Use adaptive interrupt moderation

**C. Polling (instead of interrupts)**
Under high load, polling is more efficient than handling thousands of interrupts per second.

Example:  
Linux NAPI for network cards switches to polling mode automatically.

Summary: fewer interrupts = less CPU overhead.


4. **Use DMA (Direct Memory Access)**
DMA allows devices to **transfer data directly to/from memory** without involving the CPU for each byte.

Without DMA (slow):
CPU copies every byte to memory → heavy overhead.

With DMA (fast):
CPU only tells device:
- where memory buffer is
- how much to transfer

Then hardware does the transfer.
CPU is free to do useful work while DMA runs in background.

DMA improves throughput and lowers CPU usage.


5. **Use Smarter Hardware Devices**
Smarter devices can do more work themselves, reducing OS overhead.

Examples:
- Modern NICs can compute TCP checksums automatically (offloading).
- SSD controllers handle wear leveling, garbage collection, ECC.
- RAID controllers perform parity calculations.

Let hardware do what it’s good at → free CPU cycles.


6. **Balance CPU, Memory, Bus, and I/O Throughput**
This means:  
No single part of the system should become the bottleneck.

Example:
- Fast CPU + slow disk = disk-bound
- Fast disk + slow PCI bus = bus-bound
- Fast SSD + slow memory = memory-bound

System designers balance:
- I/O channel speeds
- Memory bandwidth
- CPU processing
- Bus (PCIe) speeds
- DMA engine capability

Performance depends on _the slowest component in the I/O path_.


7. **Move User-Mode Processes/Daemons to Kernel Threads**
Kernel threads:
- Avoid user→kernel context switches
- Avoid system calls for every wakeup
- Can run with lower overhead

Examples:
- Linux `kthreadd`, `ksoftirqd`, `kswapd`
- Filesystem daemons like journaling moved into kernel
- Storage stack workers (e.g., block I/O schedulers) run as kernel threads

Moving heavy I/O handling into kernel space reduces overhead and speeds up operations.