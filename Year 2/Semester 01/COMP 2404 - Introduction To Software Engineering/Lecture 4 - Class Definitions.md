#### Imperative to Object Oriented  

C++ was once known as C with classes.  
	Classes provide an Object Oriented way of organizing data and functions related to that data.  
We will start by writing the code Imperatively  
	C uses imperative style.  
	We will convert it to Object Oriented code.

**Encapsulation**
	We don’t give access to information in unnecessary ways.  
	Only functions belonging to the class had access to private member variables.

Abstraction
Inheritance
Polymorphism

---
#### Access Specifiers  
 
**Public access**  
	Class member is visible to all objects and global functions

**Protected access**  
	Class member is visible by subclasses only  
	Different from Java  
	Make use of this only when using inheritance

**Private access**  
	Not visible to other classes or global functions  
	Visible to other members of the same class

---
#### Class Members  

**A Class in C++ should consist of 2 files:**  
	**A header file (using the .h extension) contains the class definition.**  
		Data member declarations.  
			string name;  
			string id;  
			etc.  
		Member function prototypes (usually not the code!)  
			void print();  
			bool isPassing();  
	**A source file (using the .cc extension)**  
		This contains the member function implementation (the actual code)  
		Static data member initializations  
		Related global functions

---
#### Variable Scope  

Variable scope refers to where in the program a variable is visible.  

**Block scope**  
A variable declared within a block has block scope.  
	Visible within that block and all inner blocks (unless shadowed).  
	Once we exit the block, the variable disappears and its value is discarded.  
	Variables in inner blocks can hide variables in outer blocks.  
		Shadowing.  
	If variables in nested blocks have the same name, the innermost block variable is the one used.  
		Try to avoid this - use unique identifiers when possible.  
	Can always use the unary resolution operator to access a global value.  
	Other shadowed variables remain invisible, unless blocks are namespaces

**File scope**  
A variable in File scope:  
	Is declared outside of all blocks  
	Visible everywhere in that file
		Global variables
		Global functions  

Such a variable can be accessed from another file using the extern keyword.  
	Without extern the compiler will think it is a new variable declaration.

Function scope for labels.  

Function prototype scope for parameters.  
	`int foo(int n, int x[n])`


---
#### Namespaces

**What is a Namespace?**  
	Not a class! Not a package! Has properties of both.  
	Closest equivalent is Java package, but more flexible.  
	It is the definition of a (named) scope.  

To use an element from a namespace you must scope it in by either  
	Using the using keyword  
	Use the scope resolution operator ::

A namespace may be unnamed, then it is automatically scoped in.  
	Has only internal linkage.  
	Visible only to the current translation unit  
		Current source and `#include-d` headers.  
		I.e., everything that makes this object file.  

This is like a global variable, but only for a select group of files.