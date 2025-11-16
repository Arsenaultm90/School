**Templates** in C++ allow you to write **generic code** — code that works with **any data type** without rewriting it for each type.

Think of templates as **blueprints**:
- You write the algorithm **once**.
- You can use it with `int`, `double`, `string`, or even your own classes.
- The compiler generates the specific code for the types you actually use.

##### **Why use templates?**
- Avoid code duplication
- Achieve **type safety** without using `void*` pointers
- Enable generic programming (STL is heavily template-based)


---
#### **Function Templates**

Function templates allow you to write a function that works with **any type**.

Syntax:
```
template <typename T>
T add(T a, T b) {
    return a + b;
}
```

Usage:
```
int main() {
    cout << add(3, 4) << endl;       // T = int
    cout << add(2.5, 3.1) << endl;   // T = double
    cout << add(string("Hi "), string("There")) << endl; // T = string
}
```
- The compiler **creates versions of `add`** for `int`, `double`, `string`, etc.
- `typename` can also be written as `class` (they are interchangeable in this context).


---
#### **Class Templates (Generics in Java)**

Class templates allow you to create **generic classes** that work with any type.

Syntax:
```
template <typename T>
class Box {
    T content;
public:
    Box(T c) : content(c) {}
    void display() { cout << content << endl; }
};
```

Usage:
```
int main() {
    Box<int> intBox(123);
    Box<string> strBox("Hello");

    intBox.display();  // 123
    strBox.display();  // Hello
}
```
T is replaced with the type specified when creating the object.
Similar to Generics in Java.


---
#### **STL `vector` class**

The C++ Standard Template Library (STL) uses **class templates extensively**.  
`vector` is a **dynamic array** that can store any type.

Basic Declaration:
```
#include <vector>
#include <iostream>
using namespace std;

int main() {
    vector<int> numbers;       // vector of ints
    vector<string> names;      // vector of strings

    numbers.push_back(10);
    numbers.push_back(20);
    numbers.push_back(30);

    cout << numbers[1] << endl;  // 20
}
```

Features:
- `push_back()` — add element at the end
- `size()` — number of elements
- `[]` operator — access by index
- `begin()`, `end()` — iterators for loops
- `erase()` — remove element
- `insert()` — insert element

##### Characteristics:
1. **Dynamic resizing**
    - `vector` grows automatically when you add elements
    - No need to allocate a larger array manually

2. **Automatic memory management**
    - When the `vector` goes out of scope, memory is freed automatically
    - No `delete[]` needed

3. **Rich interface**
    - `push_back()`, `pop_back()`, `insert()`, `erase()`, `clear()`, `size()`, `empty()`, etc.

4. **Supports iterators**
    - Enables range-based loops and algorithms (`sort`, `find`, etc.)

5. **Type-safe and generic**
    - `vector<T>` can hold any type (built-in or user-defined)
    - Type is known at compile-time → no casts needed

6. **Optional bounds checking**
    - `v.at(i)` throws an exception if `i` is out of bounds (safer than `[]`)