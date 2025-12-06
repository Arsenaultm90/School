#### System Calls

• Programming interface to the services provided by the OS  
• Typically written in a high-level language (C or C++)  
• Programs use a high-level Application Programming Interface (API)  
	• Though can still do direct system call  
• Three most common APIs are:  
	• Win32 API for Windows,  
	• POSIX API for POSIX-based systems (UNIX, Linux, and Mac OS X)  
	• Java API for the Java virtual machine (JVM)


---
#### Types of System Calls

**Process control**  
	• create process, terminate process  
	• end, abort  
	• load, execute  
	• get process attributes, set process attributes  
	• wait for time  
	• wait event, signal event  
	• allocate and free memory  
	• Dump memory if error  
	• Debugger for determining bugs, single step execution  
	• Locks for managing access to shared data between processes

**File management**  
	• create file, delete file  
	• open, close file  
	• read, write, reposition  
	• get and set file attributes  

**Device management**  
	• request device, release device  
	• read, write, reposition  
	• get device attributes, set device attributes  
	• logically attach or detach devices

**Information maintenance**  
	• get time or date, set time or date  
	• get system data, set system data  
	• get and set process, file, or device attributes  

**Communications**  
	• create, delete communication connection  
	• send, receive messages if message passing model to host name or process name  
	• From client to server  
	• Shared-memory model create and gain access to memory regions  
	• transfer status information  
	• attach and detach remote devices

**Protection**  
	• Control access to resources  
	• Get and set permissions  
	• Allow and deny user access


---
#### **System Services (System Programs)**

 Provide **convenient environment** for development & execution

**File management**
    - Interfaces for file/dir ops: create, delete, copy, rename

**Status information**
    - Collectors: date, time, memory, disk space, users
    - Performance, logging, debugging info
    - Registry (on some OS): config storage & retrieval

**File modification**
    - Editors, parsers, converters, search tools

**Programming-language support**
    - Compilers, assemblers, debuggers, interpreters

 **Program loading & execution**
 
**Communications**
    - Virtual connections for processes, users, systems

 **Background services**
    - Launch at boot
    - Startup only OR persistent until shutdown
    - Provide: disk check, scheduling, error logging, printing
    - Run in user context → called services, subsystems, daemons

 **Application programs**
    - Not part of OS, user-launched (CLI, GUI, touchscreen)


---
#### Linker and Loader

##### What happens from source code → execution:
1. **Compilation**
    - Source code (C, C++, etc.) → compiled into **object files** (machine code fragments).
    - Object files are relocatable (can be loaded at different addresses).
2. **Linking**
    - Linker combines object files into a single **executable binary**.
    - Resolves references (e.g., function calls across files).
    - Brings in required libraries (static or dynamic).
3. **Dynamic Linking**
    - Modern systems use **Dynamic-Link Libraries (DLLs in Windows, .so in Linux)**.
    - These libraries are **loaded once into memory** and **shared by all processes**, saving memory.
4. **Loading**
    - Final executable (on disk) must be **brought into memory** to run.
    - Loader:
        - Reads executable file format (ELF in Linux, PE in Windows, Mach-O in macOS).
        - Performs **relocation**: assigns final addresses to program sections and adjusts code accordingly.
        - Passes control to the entry point (`main()` or equivalent).

**Key Takeaway**:  
The linker makes a complete executable; the loader brings it into memory and prepares it to run. Dynamic linking saves space and enables code sharing.


---
#### Why Applications are OS-Specific

- Each OS has its own **system calls** and **binary formats**.

- **Cross-platform apps**:
    - Written in **interpreted languages** (Python, Ruby) → rely on interpreter.
    - Written in **VM languages** (Java, C#) → rely on virtual machine.
    - Written in **C/C++** → must be **recompiled** per OS.

- **ABI (Application Binary Interface)** = low-level contract between compiled code and OS/hardware. It differs across OSes and architectures.

**Key Takeaway**:  
Applications depend on the OS because of system calls and binary compatibility. Cross-platform apps work by relying on interpreters or VMs, not native binaries.


---
#### Design and Implementation of OS

- **Not “solvable”**: no single correct design; depends on goals.
- **User goals**: easy, safe, reliable, fast.
- **System goals**: efficient, flexible, maintainable.
- Influenced by hardware type, intended use (desktop, server, embedded).
- **Creative software engineering task**.

**Key Takeaway**:  
OS design is goal-driven and context-specific; no universal “best” design.


---
#### Policy vs. Mechanism

- **Policy** = _What_ should be done.    
    - Example: "Switch tasks every 100 ms."
- **Mechanism** = _How_ it is done.
    - Example: "Use hardware timer to generate interrupts."
- Good OS design separates the two.

**Key Takeaway**:  
Always separate **decisions (policy)** from **implementation (mechanism)** for flexibility


---
#### Implementation

- **Languages used historically**:
    - Early OS: Assembly (fast, hardware control).
    - Later: Higher-level languages (Algol, PL/1, C, C++).

- **Modern OS**:
    - Mix of languages:
        - Assembly → hardware-dependent routines.
        - C → kernel core.
        - C++/scripting → higher-level system utilities.

- **Tradeoff**:
    - High-level languages → portable, easier to maintain.
    - Low-level → faster, but hardware-specific.

- **Emulation**: enables running OS on non-native hardware (e.g., Windows on ARM via emulation).

**Key Takeaway**:  
Modern OSes are written mostly in C, with assembly for low-level hardware; portability vs. efficiency is the central tradeoff.


---
#### Microkernel

- **Idea**: minimize what runs in kernel mode.
    - Only essential services in kernel (low-level memory mgmt, IPC).
    - Other services (drivers, file systems, networking) → run in **user space**.

- **Communication**: components talk via **message passing**.
    
- **Benefits**:
    - Easier to extend & port.
    - More reliable (less kernel code = fewer crashes).
    - More secure.

- **Drawbacks**:
    - Performance overhead (more context switches between user/kernel).

**Examples**: Mach (basis of macOS X kernel), QNX.

**Key Takeaway**:  
Microkernels are modular, reliable, and portable, but often slower due to message-passing overhead.


---
#### Modules

- Many modern OSes use **loadable kernel modules (LKMs)**.
- **Object-oriented approach**: each core component is independent.
- Modules can be **loaded/unloaded dynamically** without reboot.
- Example: Linux, Solaris.

**Key Takeaway**:  
Modular design = flexibility + efficiency; kernel can adapt without recompilation.


---
#### Hybrid Systems

- Most real OSes are **not purely monolithic or microkernel**.
    
- **Hybrid = best of both worlds**.
    - **Linux**: monolithic core + modules.
    - **Windows**: mostly monolithic, with microkernel elements for subsystems.
    - **macOS X**: hybrid → Mach microkernel + BSD Unix + kernel extensions + Aqua UI.

**Key Takeaway**:  
Real-world OSes are **hybrids**: mixing monolithic efficiency with modular flexibility and microkernel stability.


---
#### Summary

1. **System calls** = how OS provides services to programs (via C standard library interface).
2. **System services** = higher-level programs/utilities that make development and execution easier.
3. OS manages resources → services are the provisions to users/programs.
4. **Compiler → Linker → Loader** pipeline gets your program running.
5. **OS dependence**: apps rely on system calls & binary compatibility.
6. **Design**: OS must balance user goals vs. system goals.
7. **Policy vs. mechanism**: separate “what” from “how.”
8. **Implementation**: mostly C + some assembly; portability vs. efficiency.
9. **OS structures**:
    - **Monolithic** (fast, but less modular).
    - **Microkernel** (modular, secure, but slower).
    - **Modules** (dynamic, flexible).
    - **Hybrid** (practical real-world approach).


|**Model**|**Description**|**Advantages**|**Disadvantages**|**Examples**|
|---|---|---|---|---|
|**Monolithic**|Entire OS runs in kernel mode as one large program. All services (file system, device drivers, memory, etc.) are inside kernel.|- Very fast (direct procedure calls, no message passing) - Simple to implement initially|- Hard to maintain (any bug can crash whole system) - Difficult to extend (must modify kernel and recompile)|Early UNIX, MS-DOS, early Linux|
|**Microkernel**|Minimal kernel with only core functions (low-level memory mgmt, IPC, scheduling). Other services (drivers, FS, networking) run in **user space**, communicating via message passing.|- Modular, easier to extend/port - More reliable (less code in kernel mode) - More secure (fault isolation)|- Performance overhead (frequent user ↔ kernel communication)|Mach, QNX, Minix, parts of macOS (Darwin)|
|**Modules (Loadable Kernel Modules)**|Core kernel + additional functionality as dynamically loadable modules. Mix between monolithic and microkernel.|- Flexibility (load/unload features without reboot) - Good performance (still monolithic speed) - Easier to maintain than monolithic|- Still some risk: bugs in a module run in kernel mode → crash OS|Linux, Solaris|
|**Hybrid**|Combines aspects of monolithic, microkernel, and modular approaches to balance performance, flexibility, and reliability.|- Balanced tradeoffs - Can mix speed of monolithic with modular extensions - Supports security and subsystem separation|- More complex to design & maintain|Windows NT/XP/10+, macOS X (Darwin + BSD + I/O Kit), modern Linux|
