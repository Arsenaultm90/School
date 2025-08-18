#### **Files and Unix**

In UNIX systems, **everything is treated like a file**—not just documents, but also devices such as keyboards, monitors, and even network interfaces.  
Because of this, learning file I/O in C also teaches you a lot about how UNIX itself is structured.


---
#### What is I/O?

I/O (Input/Output) is simply the **movement of bytes**:
- From a **data source** (like a keyboard or file) into your program’s memory.
- From your program’s memory into a **data sink** (like the screen or a file).

C doesn’t directly move raw bytes around by hand—it abstracts I/O as **streams**, which makes handling data more flexible.


---
#### Streams

A **stream** is just a continuous sequence of bytes that flows in or out of a program.

The operating system assigns each stream a **file descriptor**—a small integer that acts like a handle or pointer to the resource. The OS also tracks permissions (read/write) and other details.

Streams can also be **buffered**, meaning data is stored temporarily before being read or written, so the program doesn’t need to process every byte instantly.

Data sources and sinks can be many things: files, the console, other programs, or hardware devices like printers or network cards.


---
#### Standard Unix Streams

UNIX defines three standard streams that every process starts with:
- **stdin (0)**: Standard Input → usually the keyboard.
- **stdout (1)**: Standard Output → usually the screen.
- **stderr (2)**: Standard Error → also the screen, but kept separate from stdout so you can redirect output and errors independently.

This setup makes it very easy to redirect input/output when running programs in the shell.


---
#### Types of Stream Data

Although everything is bytes, we interpret those bytes differently depending on the context:
- **Text**: Bytes are assumed to represent ASCII characters.
- **Formatted text**: Bytes follow a known pattern (like the rules that `scanf()` or `printf()` expect).
- **Binary**: Raw data, which might represent numbers, structures, or any combination of bytes.

This is why sometimes you can open a text file in a normal editor, but binary files look like nonsense unless you know their format.


---
#### Stream Library Functions

C provides a set of library functions to handle streams:
- **fopen(filename, mode)** opens a file as a stream (`"r"` for read, `"w"` for write, etc.).
- **fclose(stream)** closes it and frees resources.

For moving actual data:
- **Unformatted I/O**: `fread()` and `fwrite()` transfer raw bytes.
- **Formatted I/O**: `fscanf()` and `fprintf()` read/write according to format strings (e.g., `%d`, `%s`).

Even formatted functions eventually call the lower-level unformatted ones.


---
#### Working with Files

Two key ideas when reading/writing files in C:
1. **End-of-File (EOF)**
    - Marks when no more input is available.
    - The exact value depends on the OS, but C provides `feof()` to test for it.

2. **File Pointer**
    - Keeps track of where you are in the stream.
    - Automatically moves forward as you read/write.
    - You can check the current position with `ftell()` or move around with `fseek()`.

This lets you process files sequentially or jump around randomly.


---
#### System Calls vs Library Functions

At a lower level, the operating system provides **system calls** (`open`, `read`, `write`, `close`). These are powerful but slow, because each call requires switching into kernel mode.

C’s **standard library functions** (`fopen`, `fread`, etc.) sit on top of system calls. They are **portable** across systems and use **buffering** to minimize expensive system calls. That’s why you normally use library functions unless you need low-level control.


---
#### Buffers

A **buffer** is a temporary storage area that holds data before sending it onward.
- Without buffers, your program would need to constantly make system calls for every byte, which would be very inefficient.
    

**Flushing a buffer** means pushing all its data out immediately. This happens automatically in some cases, but you can also force it with `fflush()`.

 **Types of buffering:**
- **No buffering**: Data is written immediately (common for errors or keyboard input).
- **Block buffering**: Data is collected until the buffer is full, then written.
- **Line buffering**: Data is written when a newline character (`\n`) is seen, or the buffer fills.


---
#### Piping

A **pipe** connects the output of one process to the input of another. It’s just another kind of stream.

In the UNIX shell, you can use:
- `<` to redirect stdin from a file.
- `>` to redirect stdout to a file.
- `|` to pass stdout from one program into stdin of another.

Example : `cat input.txt | grep "error" > errors.txt`

Here, `cat` reads a file, `grep` filters it, and the results are redirected into `errors.txt`.

**How it works internally**:
- The shell forks two child processes.
- Sets up a pipe between them.
- Redirects stdout of one into stdin of the other.
- Waits for both to finish.

Some programs are designed to work mainly with pipes (like `grep`, `sort`, or `tee`).

**In C**, you can create pipes manually using the `pipe()` function, which gives you two file descriptors (one for input, one for output)


---
