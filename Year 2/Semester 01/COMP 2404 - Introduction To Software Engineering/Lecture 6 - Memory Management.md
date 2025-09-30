#### Stack and Heap

In C++, memory is primarily managed in **two areas**:

**Stack**
- Memory is automatically managed (allocated and freed) when functions are called and return.
- Stores:
    - Local variables
    - Function parameters
    - Return addresses
- Characteristics:
    - Fast allocation/deallocation
    - Size is limited (usually a few MB)
    - Lifespan is **automatic**; destroyed when out of scope

Example :
```
void foo() {
    int x = 10; // allocated on the stack
} // x is automatically destroyed here
```


**Heap (Free Store)**
- Memory you manually allocate and free using `new` and `delete`.
- Stores:
    - Objects or arrays that need to persist beyond a function scope
- Characteristics:
    - Slower than stack
    - Must manage manually (risk of memory leaks)
    - Size is much larger than the stack (limited by RAM)

Example :
```
int* p = new int;  // allocated on the heap
*p = 42;
delete p;          // free memory
```


**Data Segment** 
Contains global memory
	Global data members
	Static Variables
	Literals


**Code/Text Segment**
Stored the program instructions
Function Addresses



---
#### Pointers

A **pointer** is a variable that stores the **address of another variable**.

**Syntax:**
```
int a = 10;
int* ptr = &a;  // & gets the address
```

**Dereferencing:**
```
std::cout << *ptr; // 10 (value at the address)
```

**Null Pointer:**
```
int* p = nullptr;  // points to nothing
```

**Pointer Operations:**
```
int arr[5] = {1,2,3,4,5};
int* p = arr;  // points to first element
p++;           // points to arr[1]
```

Pointers are essential for **dynamic memory allocation**, function arguments, and building data structures like linked lists.



---
#### Memory Allocation

In C++, memory can be allocated **statically** or **dynamically**.

**Static allocation**
- Compiler decides memory at compile-time.
- Example:
```
int a;         // stack
int arr[5];    // fixed-size array on stack
```

**Dynamic allocation**
- Size can be determined at runtime.
- Example using `new`:
```
int* p = new int;       // single int
int* arr = new int[5];  // array of 5 ints
```

**Freeing memory**
- Always pair `new` with `delete` and `new[]` with `delete[]`.
```
delete p;       // single int
delete[] arr;   // array
```



---
#### Dynamic Array

A **dynamic array** is an array whose size is **not fixed at compile time**.

**Example:**
```
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter size of array: ";
    cin >> n;

    int* arr = new int[n];  // allocate dynamic array

    // fill array
    for(int i = 0; i < n; i++) arr[i] = i*2;

    // print array
    for(int i = 0; i < n; i++) cout << arr[i] << " ";

    delete[] arr;  // free memory
}
```

**Notes:**
- Size is determined at **runtime**.
- Must remember to **delete[]** to prevent memory leaks.
- Pointers are used to access dynamic arrays.