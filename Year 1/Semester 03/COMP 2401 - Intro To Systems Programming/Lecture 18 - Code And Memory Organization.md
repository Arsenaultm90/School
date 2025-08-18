**Why Organize Code?**
- Improve readability
- Enhance maintainability
- Optimize build efficiency (reduce recompilation)

> C lacks classes and objects — so organization depends on functional decomposition and file separation.


**Header Files (`.h`)**
- Included via `#include`
- Contents:
    - Function prototypes
    - Constants
    - `typedef` definitions
- Behave like copy-paste during preprocessing.
- **Avoid implementations** in headers to prevent duplication and redefinition errors.


**Source Files (`.c`)**
- Contain **function implementations**
- May include:
    - Forward declarations
    - File-local constants and types
- Should only include what is **used internally** if not shared.


**Design Strategy**
- Group functions by behavior or responsibility.
- Ask:    
    - _If X breaks, where do I look?_
    - _If I change Y, how many files are affected?_
    - _Do changes in Z require recompilation of unrelated code?_



---
#### Memory Organization Concepts

**Variable Properties**
1. **Data Type** – size & model of variable
2. **Identifier** – name used in code
3. **Storage Class** – affects storage location, lifetime, and linkage
4. **Scope** – where the identifier is visible
5. **Lifetime** – duration variable occupies memory
6. **Linkage** – cross-file visibility
7. **Qualifiers** – e.g., `const`, `volatile`


**Storage Classes**
Auto :
	Default for local variables (stack)
Static :
	Retains value between function calls; internal linkage
Extern :
	Declared elsewhere; external linkage
Register :
	Hints to store in CPU register


**Scope Types**
Block Scope :
	Inside `{}`; visible only within block
File Scope :
	Outside all blocks; global to file
Function Prototype :
	Parameters inside function declaration
Function Scope :
	Labels for `goto` (rarely used)


**Linkage**
Internal :
	Identifier is only visible within the file
External :
	Identifier is visible across multiple files

> **Default linkage:**  File-scope variables and functions → **external** unless marked `static`.



---
#### Libraries In C

**What is a Library?**
- A **non-executable** collection of reusable functions and data structures.
- Consists of:
    - **Header files** (`.h`) – exposed interface
    - **Object files** (`.o`) – implementation, combined into `.a` (archive)


**Benefits of Libraries**
- Encapsulate functionality
- Promote code reuse
- Avoid re-implementing known solutions
- Reduce potential for bugs


**Using a Library**
Include the header:
```
#include "names.h"
```

Compile with:
```
gcc -I./include -L./lib -lnames
```

|Option|Description|
|---|---|
|`-I`|Add custom header directory|
|`-L`|Add custom library directory|
|`-lname`|Link to `libname.a`|

**Creating a Static Library (Example)**
Folder Structure: 
```
MyLibrary/
├── include/
│   └── names.h
├── src/
│   └── names.c
├── lib/
│   └── libnames.a

```

**Steps:**
1. Write the header (`names.h`) with struct and function declarations.
2. Write the source (`names.c`) with function implementations.
3. Compile: 
```
gcc -c names.c -I ./include
```
4. Archive into a library: 
```
ar rs libnames.a names.o
```
5. Use in your programs with `#include` and `-l`/`-L`/`-I` flags.

|Part|Explanation|
|---|---|
|`ar`|Archive tool — used to create, modify, and extract from archives (.a files)|
|`r`|**Replace** or add files to the archive. If `libnames.a` exists, update it.|
|`s`|**Index** the archive (adds a symbol table) — allows faster linking|
|`libnames.a`|Name of the static library you're creating|
|`names.o`|Object file(s) to include in the library|


---
#### Summary 

|Concept|Summary|
|---|---|
|Header Files|Define interfaces; no code implementations|
|Source Files|Contain function code; organize around behavior|
|Scope vs Storage|Scope = visibility; Storage = memory location and lifetime|
|Linkage|Internal = file-only; External = cross-file|
|Libraries|Archive reusable code; include headers, link `.a` files at build time|

|Feature|Header File (`.h`)|Library (`.a`, `.so`)|
|---|---|---|
|**Purpose**|Declares _what_ exists (functions, structs)|Contains _how_ it works (compiled code)|
|**Used by**|Compiler (during preprocessing/compiling)|Linker (during the linking phase)|
|**Contents**|Function prototypes, `#defines`, `typedefs`|Machine code (compiled `.o` object files)|
|**Required for**|Knowing the interface (what functions/types to call)|Actually using those functions|
|**Analogy**|**Blueprint** (what's available to use)|**Toolbox** (the actual tools being used)|
