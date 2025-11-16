#### **Contents**
1. Faults and Exceptions
2. Error Handling
3. Exception Handling
4. Stack Unwinding
5. GDB (Debugging Exceptions)


---
#### **Faults and Exceptions**

##### Faults
A **fault** is a low-level hardware or OS event caused by illegal or unexpected behavior such as:
- Divide-by-zero
- Accessing invalid memory
- Illegal instruction
- Page fault

Faults are NOT recoverable in normal C++ programs.
They usually terminate the program unless caught by OS-level signal handlers.

Examples:
- Segmentation fault (SIGSEGV)
- Bus error (SIGBUS)
- Floating-point exception (SIGFPE)

##### Exceptions
An **exception** is a C++ language feature used to handle **run-time errors** in a controlled way.

Examples:
- Invalid argument
- Out of range
- Failure to open a file
- Logic errors

Unlike faults, **exceptions are software-defined and recoverable**.

---
#### **Error Handling**

C++ supports several styles of dealing with errors. Historically, programmers used:
##### A. Error Codes
Functions return values indicating success or error.
```
int readFile(string filename) {
    if (!exists(filename)) return -1;
    return 0;
}

int result = readFile("data.txt");
if (result == -1) {
    // handle error
}
```

**Pros:**
- Simple
- No runtime overhead

**Cons:**
- Easy to ignore (forget to check return codes)
- Clutters logic
- Does not propagate automatically


##### B. Status Flags
Class methods update an internal flag.

Example:  
`std::cin` sets `failbit`, `eofbit`, or `badbit`.
```
if (cin.fail()) {
    // error reading input
}
```

**Limitations:**
- Must manually check flags
- Flags don't indicate detailed error causes


##### C. `assert()`

Used for debugging and validating assumptions.
```
assert(x > 0);
```

**Important:**
- Removed in release builds (`NDEBUG` defined)
- Not used for run-time error handling
- Terminates the program immediately


---
#### **Exception Handling**

C++ provides a structured mechanism using three keywords:
- `throw`
- `try`
- `catch`

##### A. Throwing Exceptions
```
throw std::runtime_error("File not found");
```

You can throw objects of any type, but best practice is to throw exceptions derived from:
```
std::exception
```


##### B. Try/Catch Blocks
```
try {
    riskyOperation();
}
catch (const std::exception& e) {
    cout << "Error: " << e.what() << endl;
}
```

**Catch Types**
You can have multiple `catch` blocks:
```
try {
    doWork();
}
catch (const std::out_of_range& e) {
    // handle this specifically
}
catch (const std::exception& e) {
    // handle general exceptions
}
catch (...) {
    // catch-all fallback
}
```


##### C. Standard Exception Hierarchy
All standard exceptions derive from `std::exception`.

**Logic errors**
Programmer mistakes:
- `std::invalid_argument`
- `std::domain_error`
- `std::length_error`
- `std::out_of_range`

**Runtime Errors**
External or unpredictable environment issues:
- `std::runtime_error`
- `std::range_error`
- `std::overflow_error`
- `std::underflow_error`


##### D. Rethrowing Exceptions
```
catch (...) {
    log("error");
    throw; // rethrow same exception
}
```
Used when you need to partially handle then propagate further.


---
#### **Stack Unwinding**

This is a crucial concept for exams.

**Definition**
**Stack unwinding** is the process where C++:
1. Looks for a matching `catch` block
2. While searching, **destroys all objects** going out of scope
3. Calls destructors in reverse order of construction

Stack unwinding ensures:
- RAII works
- Resources are freed
- No memory leaks (if RAII is used properly)

**Example:**
```
class Test {
public:
    Test() { cout << "Construct"; }
    ~Test() { cout << "Destruct"; }
};

void func() {
    Test a;
    throw 5;
}

int main() {
    try { func(); }
    catch (...) { cout << "caught"; }
}
```

Output:
```
Construct
Destruct
caught
```
Note that the destructor runs even though an exception was thrown.

**Stack unwinding can be expensive**
- Destructors called for every object on the call chain
- Possible overhead in deeply nested functions
- Not ideal for real-time systems


---
#### **GDB (Debugging Exceptions)**

GDB can trace exceptions, break when thrown, and help debug crashes.

**A. Break on exception throw**
```
(gdb) catch throw
```
GDB will stop whenever an exception is thrown.

**B. Break on exception catch**
```
(gdb) catch catch
```
Stops execution whenever a catch block handles the exception.

**C. Get a stack trace**
When your program crashes:
```
(gdb) backtrace
```
This shows the full call stack—useful for diagnosing faults and uncaught exceptions.

**D. Inspect Variables**
```
(gdb) print variableName
```

**E. Run program under GDB**
```
g++ -g main.cpp
gdb ./a.out
```
The `-g` flag lets GDB show:
- line numbers
- variable names
- stack frames

Running GDB Through Terminal:
```
(gdb) catch throw
(gdb) run
(gdb) backtrace
(gdb) exit
```
