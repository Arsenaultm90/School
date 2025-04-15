##### Intro to Java
A compiled and interpreted language.
Independent and Statically Typed
OOP Paradigm


---
# Object-Oriented Programming Concepts
#### Abstraction

Abstraction involves hiding complex implementation details while exposing only the necessary features of an object. This creates simpler, more usable interfaces and helps manage complexity by allowing programmers to focus on what an object does rather than how it does it.

**Example**: A car class might expose methods like `start()`, `accelerate()`, and `brake()` while hiding the complex engine mechanics.

#### Inheritance

Inheritance allows a class (child/subclass) to acquire properties and behaviors from another class (parent/superclass). This promotes code reusability and establishes an "is-a" relationship between classes.

**Example**: A `SportsCar` class might inherit from a `Car` class, gaining all its basic features while adding specialized ones.

#### Encapsulation

Encapsulation bundles data and methods that operate on that data within a single unit (class) and restricts direct access to some of the object's components. This is implemented using access modifiers (public, private, protected) and enhances security and maintainability.

**Example**: A `BankAccount` class might keep its balance private while providing public methods like `deposit()` and `withdraw()` to manipulate it safely.

#### Polymorphism

Polymorphism allows objects of different classes to be treated as objects of a common superclass. It enables one interface to be used for a general class of actions, with specific implementations determined at runtime.

**Types**:

- **Method Overriding**: Subclass implements a method already defined in the superclass
- **Method Overloading**: Multiple methods with the same name but different parameters

**Example**: A `Shape` superclass with a `calculateArea()` method that's implemented differently by `Circle`, `Rectangle`, and `Triangle` subclasses.

These four principles work together to create modular, reusable, and maintainable code structures that model real-world relationships


---
##### Java Primitive Types

| Type    | Bit Size            | Description                                                                       |
| ------- | ------------------- | --------------------------------------------------------------------------------- |
| Byte    | <center>8</center>  | Stores whole numbers from -128 to 127                                             |
| Short   | <center>16</center> | Stores whole numbers from -32,768 to 32,767                                       |
| Int     | <center>32</center> | Stores whole numbers from -2,147,483,648 to 2,147,483,647                         |
| Long    | <center>64</center> | Stores whole numbers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| Float   | <center>32</center> | Stores fractional numbers. Sufficient for storing 6 to 7 decimal digits           |
| Double  | <center>64</center> | Stores fractional numbers. Sufficient for storing 15 to 16 decimal digits         |
| Boolean | <center>8</center>  | Stores true or false values                                                       |
| Char    | <center>16</center> | Stores a single character/letter or ASCII values                                  |


---
##### Operators and Keywords

**New :** 
	The new operator _instantiates a class by allocating memory for a new object_ and returning a reference to that memory.

**Super :** 
	The `super` keyword refers to superclass (parent) objects.
	It is used to call superclass methods, and to access the superclass constructor.

**JVM Memory :**
	Stack, Heap, Static, Free

