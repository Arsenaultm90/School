#### Building Stages 

The C build process transforms source code (`.c` files) into an executable program through several distinct stages:

**Stages:**
1. **Preprocessing**
	**Purpose**
	- Handles `#` directives (e.g., `#include`, `#define`, `#ifdef`)
	- Produces a `.i` file (pure C code with all macros and includes expanded)
	
	**Common Directives**
	- `#include` – include other files
	- `#define` – macro definitions
	- `#ifdef`, `#ifndef`, `#endif` – conditional compilation

2. **Compilation**
	**Purpose**
	- Converts preprocessed code into **assembly code**
	- Performs **syntax checking**, **semantic analysis**, and **optimization**
	
	**Output**
	- A `.s` file: human-readable assembly code

3. **Assembly**
	**Purpose**
	- Converts assembly code into **machine code**
	- Produces an **object file** (`.o`), which is not yet executable

4. **Linking**
	### **Purpose**
	- Combines multiple `.o` files and libraries into a **final executable**
	- Resolves **symbol references** (e.g., function calls between files)
	
	**Static vs Dynamic Linking**
	- **Static Linking**: All code is copied into the executable
	- **Dynamic Linking**: References shared libraries (e.g., `libc.so`) at runtime


**Object File**  
	Header Data: Metadata about the file format, architecture, and compilation settings.  
	Machine Code: Instructions compiled from one translation unit, but not yet executable.  
	Symbol Table:  
		Lists defined functions and global variables with their addresses.  
		Contains unresolved references (placeholders) to be filled in during linking.

**Linking Libraries**
1. Libraries are an archive with multiple object files  
2. Include the header file:  
	Creates placeholder symbols in the object code symbol table  
3. Link the object file / library  
	Fills in the placeholders with addresses to functions
`gcc -o my_exec src.o -lm`


---
#### Flags

|Flag|Description|
|---|---|
|`-g`|Include debug symbols|
|`-O0`–`-O3`|Optimization levels|
|`-Wall`|Enable all common warnings|
|`-Werror`|Treat warnings as errors|
|`-std=c11`|Use C11 standard|

• gcc -E: Stop to show expanded source code  
• gcc -S: Stop to show assembly code  
• gcc -c: Stop to show object code  
• gcc -o: Link object files into the specified output executable

objdump lets us view our object file contents.  
• objdump -t: Show symbol table  
• objdump -d: Disassemble machine code instructions

