Chapters 1 - 6
Content :
1. Slides
2. Book
3. Quizzes


**Process States :**
- **New** → being created.
- **Running** → instructions executing.
- **Waiting** → waiting for event (I/O, signal).
- **Ready** → waiting for CPU.
- **Terminated (Zombie)** → finished execution.

**Process Interrupted by I/O System Call:**
	Waiting -> Ready -> Executing

**Unique Transition Order:**
	The **ordering** of certain transitions is ambiguous because:
	- Interrupt handling sequence varies by implementation
	- Some transitions are logically independent (no happens-before relationship)
	- Scheduler policies introduce additional ordering flexibility
	**"The order isn't unique because there's no strict happens-before relationship between the interrupt preempting P1 and the I/O completion unblocking P0 - these are logically independent events that occur 'simultaneously' from the OS's perspective, and different implementations or observation points might record them in different orders."**

Process state transitions are _not unique_ because the exact sequence of transitions depends on how the operating system’s scheduler and I/O handling are implemented.

##### **Definitions :**
**Multiprocessing:** 
	Truly running multiple processes at the same time on separate cores.

**Multitasking:** 
	The OS makes it _appear_ that multiple programs are running at once by **rapidly switching a single CPU** between processes.

**Pre-emptive:** 
	The operating system can interrupt (or _preempt_) a currently running process **before it finishes**, so another process can use the CPU.

**Inodes store metadata:**
- File size
- Owner
- Permissions
- Timestamps
- Pointers to data blocks
**Important:** File names are stored in the **directory entry**, not in the inode.

**File Systems in Linux:**
- **File descriptor:** A small integer returned when you open a file.
- **System calls:** Used to open, read, write, and close files.
- **Inode:** Data structure that stores metadata about a file (but not its name).

**Directory Entries:**
	Directories are special files that contain a list of entries mapping filenames to inode numbers. When you access a file path, the kernel walks through each directory component, looking up each name to find its inode.

**Direct Pointers:**
	Contain pointers to blocks of memory defined by Linux. (1 read)

**Indirect Pointers:**
	A block containing pointers to memory outside the range of the direct pointers. (1 read for block + 1 read for memory)