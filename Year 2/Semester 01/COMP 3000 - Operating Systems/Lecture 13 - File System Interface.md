# **File Concept**

### **What a file is**
- A **named collection of related information** stored on nonvolatile storage (HDD, SSD/NVM, optical, etc.).
- OS provides a **uniform logical abstraction** → hides hardware details.
- A file is the **smallest unit** to which data can be written on secondary storage.

### **File contents**
Files may contain:
- Text
- Executables
- Source code
- Images, audio, video
- Structured or unstructured data

### **OS examples**
- UNIX/Linux uses `/proc` — exposes system info as files.

### **File structure**
- Sequence of bytes (UNIX), lines, records, etc.
- Structure depends on creator and application (not OS, except executables).



---
# **File Attributes**

Common attributes (stored in the directory entry):

| Attribute      | Description                          |
| -------------- | ------------------------------------ |
| **Name**       | Human-readable file name             |
| **Identifier** | Unique internal ID (inode #, FID)    |
| **Type**       | Needed on OSs with typed files       |
| **Location**   | Pointer(s) to physical device blocks |
| **Size**       | Current + possible max size          |
| **Protection** | Access control info                  |
| **Timestamps** | Create, last accessed, last modified |

Extra attributes may include checksum, encoding, etc.
Directories store **names → identifiers**; identifiers point to full metadata.



---
# **File Operations**

Seven fundamental operations:
1. **Create**
    - Allocate space + create directory entry.
2. **Open**
    - Look up file in directory
    - Load metadata into open-file table
    - Return file handle
3. **Write**
    - Write at current offset
    - Advance write pointer
4. **Read**
    - Read at current offset
    - Advance read pointer
5. **Reposition/Seek**
    - Change file offset (no I/O required)
6. **Delete**
    - Remove directory entry
    - Free blocks
    - Handle hard links (delete only when last link removed)
7. **Truncate**
    - Erase data but keep attributes

### **Other operations**
Rename, append, get/set attributes.

### **Why open()?**
Avoid repeated directory lookups.  
Open files stored in:
- **System-wide open-file table**
- **Per-process open-file table**

Each per-process entry → pointer into system-wide entry.

### **Tracking info for open files**
- **File pointer** (per-process)
- **File-open count**
- **File location metadata**
- **Access rights**



---
# **File Locking**

Locks control concurrent access.
Types:
- **Shared (read)** → multiple readers
- **Exclusive (write)** → only one writer

Two enforcement modes:
- **Mandatory** (OS enforces) — common on Windows
- **Advisory** (program must cooperate) — common on UNIX

Can cause deadlocks.



---
# **File Types**

- Often indicated by **file extension** (e.g., `.exe`, `.txt`, `.jpg`).
- Windows/macOS use extensions; UNIX treats files as **byte sequences**.
- Some OSs identify type via **magic numbers** inside file.



---
# **File Structure**

- Some OSs support multiple file structures (complex).
- UNIX: **files are just sequences of bytes** → simple, versatile.
- Internal structure must exist for executables (format known by loader).

### **Internal layout**
- Disk uses fixed-size **blocks**; last block often partially empty → **internal fragmentation**.



---
# **Access Methods**

### **Sequential Access**
- Read/write next
- Most common (editors, compilers)
- Based on tape model

### **Direct Access (Random Access)**
- File = array of fixed-size records or blocks
- Read(n) or position(n) operations
- Supports databases, reservation systems
- Uses **relative block numbers** (starting from 0)

### **Indexed Access**
- Uses index structure → pointer to blocks
- Can support multi-level indices when file is large
- Like a book index → search index, then fetch block


---
# **Directory Structure**

Directory = table mapping **names → metadata (FCB/inode)**.

### Required directory operations:
- Search for file
- Create file
- Delete file
- List directory
- Rename file
- Traverse filesystem

### **1. Single-Level Directory**
- All files in one directory
- Easy but terrible for multiple users
- Naming conflicts likely

### **2. Two-Level Directory**
- Each user has UFD (user file directory)
- Master File Directory (MFD) maps users → UFD
- Solves naming conflict but poor for sharing

### **3. Tree-Structured Directory**
- Most common (UNIX, Windows)
- Allows hierarchical organization (subdirectories)
- Each process has a **current working directory**
- Pathnames:
    - **Absolute**: starts from root (`/home/matt/foo`)
    - **Relative**: from CWD (`foo/bar`)

### Directory deletion
- Delete only if empty **or** delete recursively (policy decision).

### **4. Acyclic-Graph Directory**
- Allows **shared directories/files** via links
- Supports collaboration
- Hard links or symbolic links

Challenges:
- Multiple pathnames to same file
- Deletion must handle shared references
- Reference count solves most issues
- Symbolic links may become dangling

### **5. General Graph Directory**
- Allows cycles
- Complicated traversal and deletion
- May require **garbage collection**
- Usually avoided; many OSs restrict linking to avoid cycles



---
# **Protection**

Need to protect:
- Files
- Directories (listing, searching, creation, deletion)

## Types of access:
- Read
- Write
- Execute
- Append
- Delete
- List
- Change attributes

### **Access Control Mechanisms**

**A. Access Control Lists (ACLs)**
- Per-file list of `(user, permissions)`
- Precise but can become long

**B. Owner / Group / Other model (UNIX)**
- Three classes: **owner**, **group**, **others**
- Three bits each: `rwx`
- Example: `rw-rw-r--`

UNIX allows optional extended ACLs.

**Windows**
- Uses fine-grained ACLs via GUI.

**C. Password protection**
- Per-file passwords (rare now)
- Not scalable; insecure



---
# **Memory-Mapped Files**

### **Concept**
- Map file blocks directly into a process’s **virtual memory**.
- File I/O becomes **memory loads/stores**.

### **How it works**
- First access → page fault → bring block into memory
- Subsequent accesses = normal memory operations
- Writes:
    - Buffered in memory
    - Written back on close or periodically

### **Advantages**
- Huge speed gains
- Eliminates read()/write() overhead
- Used for shared memory between processes

### **Sharing**
Multiple processes can map the same file → share memory pages.

### **Windows API**
- `CreateFile()`
- `CreateFileMapping()`
- `MapViewOfFile()`
- `UnmapViewOfFile()`

Used to implement shared memory.

