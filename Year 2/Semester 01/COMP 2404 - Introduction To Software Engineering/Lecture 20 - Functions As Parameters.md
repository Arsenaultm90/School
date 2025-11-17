#### **Function Types and Variables**

In C++, **a function has a type**, just like variables do.

Example function:
```
int add(int a, int b);
```

This function has type:
```
int(int, int)
```
This means:
    it returns an int
    it takes two int parameters


##### Function Pointers
You can store a function **in a variable** using a function pointer:
```
int add(int a, int b) { return a + b; }

int (*fp)(int, int) = add;
```
Explanation:
- `(*fp)` means fp is a pointer to a function
- `(int, int)` means the function takes two ints
- `int` is the return type

Call it like a normal function:
```
int result = fp(2, 3);  // 5
```
Function pointers are the core mechanism used to pass functions as arguments.


---
#### **Functions As Parameters**

You can pass:
- a **function pointer**
- a **lambda**
- a **functor** (function object)


##### Passing a Function Pointer
**Function to be passed:**
```
int square(int x) { return x * x; }
```

**Function receiving the function pointer:**
```
int apply(int (*func)(int), int value) {
    return func(value);
}
```

**Call:**
```
cout << apply(square, 5); // 25
```

**Cleaner Syntax (Using `using` or `typedef`)**
Instead of writing:
```
int (*func)(int)
```

Define the function type:
```
using FuncType = int(*)(int);
```

Then:
```
int apply(FuncType func, int value) {
    return func(value);
}
```


---
#### **Lambda Functions**

Lambdas are anonymous inline functions.

Example:
```
[ captures ] ( parameters ) -> return_type {
    body
};

auto lambda = [](int x) { return x + 10; };
```

Passing it as a parameter:
```
int apply(auto func, int value) {
    return func(value);
}
```

The `[]` (square brackets) are called the **capture list**.
They define **which variables from the surrounding scope** the lambda is allowed to use.
Lambdas have unique types, not function-pointer types, unless they have **no captures**.


A. Passing a lambda with **no captures**
```
int apply(int (*func)(int), int x) {
    return func(x);
}

cout << apply([](int x) { return x * 3; }, 4);
```
This works because a capture-less lambda can convert to a function pointer.

B. Passing a lambda **WITH captures**
These cannot convert to function pointers.

Example:
```
int offset = 10;
auto lam = [offset](int x){ return x + offset; };
```

To accept this, the function must use a **template**:
```
template<typename F>
int apply(F func, int x) {
    return func(x);
}

cout << apply(lam, 5); // works!
```
Templated functions are the **most flexible** way to pass lambdas.


---
#### **Functions As Objects (Functors)**

In C++, functions can be represented by **objects that overload `operator()`**.
These are called **functors** or **function objects**.

Example:
```
struct Multiply {
    int operator()(int a, int b) const {
        return a * b;
    }
};
```

Use it like a function:
```
Multiply m;
cout << m(3, 4); // 12
```


Functors can:
- store state
- behave like functions
- be optimized better than function pointers

Example with state:
```
struct Adder {
    int offset;
    Adder(int off) : offset(off) {}

    int operator()(int x) const {
        return x + offset;
    }
};
```

Call:
```
Adder add5(5);
cout << add5(10); // 15
```


**Using `std::function` for Function Objects**
`std::function` is a general-purpose wrapper that can store:
- function pointers
- lambdas
- functors

Example:
```
#include <functional>

void process(std::function<int(int)> f) {
    cout << f(3);
}
```

Call:
```
process([](int x){ return x + 1; });
process(square);
process(Adder(10));
```
This is the most flexible, but has overhead compared to templates.

