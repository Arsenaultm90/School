
An operating system acts as an intermediary between the user of a computer and the computer hardware. The purpose of an operating system is to provide an environment in which a user can execute programs in a convenient and efficient manner.

A more common definition, and the one that we usually follow, is that the operating system
is the one program running at all times on the computer—usually called the kernel. Along with the kernel, there are two other types of programs: system programs, which are associated with the operating system but are not necessarily part of the kernel, and application programs, which include all programs not associated with the operation of the system.

An **Operating System (OS)** has three main purposes:
1. **Convenience / Abstraction**
    - Provide a **middle ground** (abstraction layer) between hardware and applications so users/programs don’t need to deal with raw hardware.
    - Example: Instead of coding disk sectors, you just call `fopen()` or `read()`.
2. **Control / Resource Management**
    - Control and manage hardware resources (CPU, memory, I/O devices).
    - Includes scheduling, process management, file systems, device drivers, etc.
3. **Efficiency / Utilization**
    - Make sure the system’s resources are used efficiently and fairly.
    - Example: Multiprogramming lets many processes share CPU and memory without waste.

A computer system can be divided roughly into four components: 
	The Hardware 
	The Operating System 
	The Application Programs
	A User

---
#### User View

The user’s view of the computer varies according to the interface being used. Many computer users sit with a laptop or in front of a PC consisting of a monitor, keyboard, and mouse.

![[Screenshot 2025-09-09 at 7.48.18 AM.png|500]]


---
#### System View

From the computer’s point of view, the operating system is the program most intimately involved with the hardware. In this context, we can view an operating system as a resource allocator.

An operating system is a control program. A control program manages the execution of user programs to prevent errors and improper use of the computer. It is especially concerned with the operation and control of I/O devices.


---
#### Computer-System Organization

A modern general-purpose computer system consists of one or more CPUs and a number of device controllers connected through a common bus that provides access between components and shared memory. Each device controller is in charge of a specific type of device.

Operating systems have a device driver for each device controller. This device driver understands the device controller and provides the rest of the operating system with a uniform interface to the device. The CPU and the device controllers can execute in parallel, competing for memory cycles.

![[Screenshot 2025-09-09 at 8.04.28 AM.png|500]]


---
#### Interrupts

Hardware may trigger an interrupt at any time by sending a signal to the CPU, usually by way of the system bus. Interrupts are used for many other purposes as well and area key part of how operating systems and hardware interact.

When the CPU is interrupted, it stops what it is doing and immediately transfers execution to a fixed location. The fixed location usually contains the starting address where the service routine for the interrupt is located. The interrupt service routine executes; on completion, the CPU resumes the interrupted computation.

![[Screenshot 2025-09-09 at 8.09.38 AM.png|700]]

1. Device triggers an interrupt.
2. CPU saves PC and flags.
3. CPU reads interrupt number → looks up ISR address in IVT.
4. CPU jumps to ISR (fixed location).
5. ISR executes.
6. ISR executes **return-from-interrupt** instruction.
7. CPU restores saved state → resumes original program.

- **Vector = an address to jump to**
- **IVT = table of vectors, one for each interrupt**

Most CPUs have two interrupt request lines: 
	Non-maskable interrupt, which is reserved for events such as unrecoverable memory errors. 
	Maskable interrupt that can be turned off by the CPU before the execution of critical instruction sequences that must not be interrupted. The maskable interrupt is used by device controllers to request service.

