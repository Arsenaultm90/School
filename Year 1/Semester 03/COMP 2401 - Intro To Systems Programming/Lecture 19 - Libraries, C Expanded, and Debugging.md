#### Libraries

**Definition**:
- A reusable set of functions used across programs
- Not executable → no `main()` function
- Contains:
    - **Header files (.h)**
    - **Object files (.o)** → archived into `.a`

**Purpose**:
- Save time (reuse)
- Minimize errors (solved mistakes)
- Use optimized solutions


**Using Libraries**
-**Include header file**
    - Default: `/usr/include`
    - Custom: `gcc -I ./my_headers`
        
-**Link object code**
    - Example: `gcc -lname` → links `libname.a`
    - Default: `/usr/lib`
    - Custom: `gcc -L ./my_libs`


 **Making a Library (Example: `names`)**
**Steps**:
1. Write header (`names.h`)
2. Write source (`names.c`)
3. Compile to object code
4. Archive with `ar rs` into `libnames.a`
5. Place `.a` in `/lib/` and `.h` in `/include/`


---
#### Common C Versions

- **C89/C90**: First standard, widely used, missing modern features
- **C99**:
    - Declare vars in for loops
    - `stdbool.h`, `stdint.h`
- **C11**:
    - `threads.h`, `stdatomic.h`
    - Safer string functions (`strncpy_s`, etc.)
- **C23 (newest)**:
    - `nullptr` instead of `NULL`
    - Safer `_s` functions
    - `auto`, `typeof` for type inference
    - Better Unicode support


---
#### Common Libraries & Functions

##### `math.h` (link with `-lm`)
- `sqrt(x)`, `pow(x, y)`
- `sin(x)`, `cos(x)`, `log(x)`
- `ceil(x)`, `floor(x)`

##### `stdbool.h`
- Defines `bool`, `true`, `false`

##### `stdint.h`
- Fixed-width integer types:
    - `int8_t`, `int16_t`, `int32_t`, `int64_t`
    - `uint8_t`, etc.

##### `string.h`
- `strstr(str, sub)` → find substring
- `memset()`, `memcpy()` → set/copy memory
- `strtok()` / `strtok_r()` → split string
- Often combined with **dynamic memory** (`malloc`, `calloc`, `realloc`)


---
#### Debugging with GDB

**Steps**:
1. Compile in debug mode:
```
gcc -g -o prog prog.c
```
2. Run: `gdb ./prog`
3. Optional: `gdb -tui ./prog` (visual)
4. Can integrate with VS Code

**Commands**:
- `break` → set breakpoint
- `step` → step line by line
- `continue` → run until breakpoint
- `watch var` → stop when variable changes
- `list` → show nearby code
- `backtrace` → show call stack
- `frame` → inspect specific stack frame