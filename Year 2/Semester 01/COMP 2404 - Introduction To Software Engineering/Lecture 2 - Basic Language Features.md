#### Data Types

**Primitive :**
	int
	float
	char
	bool
	double

**Aggregate :**
	classes - class Student { }
	structs - struct Student { }

**Memory Address :**
	pointers - Student* stu = new Student

**Variables Have :** 
	Name
	Type
	Address
	Value


---
#### Memory

**Two main places for memory :**
	Call Stack
	Heap

**Call Stack**
Any local variables are stored in that stack frame. 
These variables are deleted automatically when we return from a function.

**Heap**
Variable declared with new goes on the Heap  
	New keyword returns a pointer  
	A pointer contains a memory address  
	Must dereference `(*)` the pointer to access the int value  
	Variable remains in memory until delete is called on the pointer
```
int* x = new int;  
*x = 18;  

delete x
```


---
#### Declaring Variables

**Statically Allocated :**
	`int x`
	`float y`

The variable has memory allocated where it is declared  
Could be on the function call stack or as data in a struct or class  
The containing struct or class may be statically or dynamically allocated  
This variable is deleted automatically

**Dynamically Allocated :**
	`int *x = new int;`
	`float *y = new float;`

The variable has memory allocated on the heap  
Deleted when delete is called


---
#### Classes and Structs

**Structs**
- Originally from C, a `struct` is a way to group **related variables** together.
- In C++, `structs` can also have **methods, constructors, destructors**, just like classes.

Syntax :
```
struct Point {
    int x;
    int y;

    void print() {
        std::cout << "(" << x << ", " << y << ")\n";
    }
};
```

Access
- **Default member access is public**.
- That means all variables and methods are accessible outside the struct unless you explicitly use `private:` or `protected:`.

```
Point p;
p.x = 10;  // OK
p.y = 20;
p.print();
```



**Classes**
- Classes are the main way to define **objects** in C++.
- They encapsulate **data (attributes)** and **behavior (methods)**.

Syntax :
```
class Point {
private:
    int x;  // private by default
    int y;

public:
    Point(int xVal, int yVal) : x(xVal), y(yVal) {}

    void print() {
        std::cout << "(" << x << ", " << y << ")\n";
    }

    void setX(int xVal) { x = xVal; }
    int getX() { return x; }
};
```

Access
- **Default member access is private**.
- Use `public:` to expose methods or variables.

```
Point p(10, 20);
p.print();        // OK
p.setX(15);       // OK
// p.x = 15;      // ❌ Error: x is private
```


---
#### Operators

**Types of operators :**  
	Arithmetic  `+ - * / % ++ --`  
	Relational (logical, returns bool) `== <= >= != < >`  
	Logical (returns bool) `&& || !`  
	Bitwise `~ & | ̂ << >>`  
	Assignment Operators `= += -= *= /= %=`  
	Conditional `? :` 

**Arity :**  
The number of arguments  
	unary, binary, ternary  

**Precendence :**  
	The order in which operators execute  
	It is not simply left to right – BEDMAS  

**Associativity :**  
	The order in which operators of the same precedence execute  
	Left-to-right or right-to-left

Arithmetic operators have left to right associativity  
	`a / b / c / d;  // the order will affect the outcome`  

Assignment operators have right to left associativity  
	`a = b = c = d;  // all receive the value in d`  

Prefix vs postfix operators  
	`++x vs x++`  
	prefix is slightly faster


---
#### C++ Terminology

**Expression** 
	A sequence of operations that resolve to a value
	`2 + 2 - 3`

**Statement**
	An instruction or command terminated by a semi-colon  
	Can be an expression – return value can be used or discarded  
	Can be a function
	`v = 6 + 2;`  
	`getValue();`  
	`setValue(4);`

**Control Flow Statements**
	Conditional  
		if-else  
	Selective  
		switch  
	Iterative  
		do-while, while, for  
	Jump  
		break, continue

**Blocks** 
```
21  
Blocks and Local Variables  
int x = 8;  
for (int i = 0; i < 10; i++){  
int x = i;  
}  
cout<<x<<endl;
```

**Scope**
	Block scope  
		Declared in a block  
		Local to that block  
		“local variables”  
	Global scope / file scope  
		Declared outside of any block  
		“global variables”  


---
#### Standard I/O Streams

`#include <iostream>`  
	Allows standard input and output in the std namespace

cout – member of the ostream class  
	An object with reference to standard output (console)  
	You can change the output stream associated with cout (to a string for example)

cin – member of the istream class - standard input

cerr – member of the ostream class - standard error output (console, or you can  
set to a log file)


---
#### Functions

**Global functions**  
	C exclusively uses global functions.  
	Defined outside of any block (except a namespace).  
	ICalled from any function and any class in the program.  
	Example: main().

**Member functions**  
	Java exclusively uses member functions.  
	Defined within a class – behaviour of that class.  
	Called by an object of that class, however  
	static (class) functions can be called on the class itself.

**Return Values vs Output Parameters:**
Return values:  
	Allow for more elegant code (functions can be nested in expressions).  
	Are simple and intuitive to use.  
	Multiple values can be returned using structs  
	Memory ownership is not always clear

Output parameters:  
	Allows for existing objects to be modified.  
	Can easily return multiple pieces of data  
	Memory ownership is clear without requiring documentation

**Parameters**  
	Space is allocated on the function call stack.  

Parameters can be passed in using  :
	Pass-by-value:  
		The value passed in is copied into a local variable.  
		The value passed in can be a variable or expression.  
		The function can only modify the local value - the original value is untouched.
	Pass-by-reference:  
		The memory address of a variable is copied and passed into the function.  
		Must be a variable or an expression that evaluates to a variable.  
		This address “points” to the original value, allowing us to modify the original  
		value.


---
#### Pass by Reference/Value

**Pointers :**  
	Powerful.  
	Somewhat natural.  
	Easy to make mistakes with - segmentation fault, or worse, NULL reference (bad memory).  

**References :**  
	Same thing “under the hood” as pointers.  
	It is a memory location.  
	Syntactically treated as a variable.  
	Less versatile than pointers, but easier to use.  
	Supposed to protect against NULL references


---
#### Const

**Const Variables:**
```
const int x = 10;
```
- **Purpose:** Makes the variable **read-only**, it cannot be modified after initialization.
- **Effect:** Any attempt to assign to `x` later will cause a compile-time error.


**Const Pointers:**
Point To A Const Value:
```
const int* ptr = &x;
```
- **Meaning:** The **value being pointed to is read-only**, but the pointer itself can point elsewhere.
- **Effect:** You cannot do `*ptr = 5;` but you can do `ptr = &y;`.

Const Pointer:
```
int* const ptr = &x;
```
- **Meaning:** The **pointer itself cannot change**, but the value it points to can.
- **Effect:** `ptr = &y;`  error, but `*ptr = 5;` allowed.

Const Pointer To Const:
```
const int* const ptr = &x;
```
- **Meaning:** Neither the pointer nor the value it points to can change.
- **Effect:** Both `*ptr = 5;`  and `ptr = &y;` are errors.


**Const Function Parameters:**
```
void print(const string& s) { ... }
```
- **Purpose:** Prevents the function from modifying the argument.
- **Effect:** Inside the function, you cannot change `s`.
- **Benefit:** Useful for **pass-by-reference** to avoid copying while protecting data.


**Const Member Functions:**
```
class MyClass {
    int x;
public:
    int getX() const { return x; }
};
```
- **Purpose:** Guarantees the member function will **not modify any member variables** of the object.
- **Effect:** You can call this function on **const objects**:
```
const MyClass obj;
obj.getX(); // allowed
obj.setX(5); // not allowed if setX is not const
```


**Const Return Type:**
```
const int& getValue() { return x; }
```
- **Purpose:** Prevents the caller from modifying the returned value.
- **Effect:** If you return a reference or pointer, the caller cannot change the underlying value.