Polymorphism literally means “many forms.” In programming, it allows objects of different classes to be treated as objects of a common base class, but behave differently depending on their actual derived type.

Key points:
- It allows **code generalization**, e.g., a function can operate on a base class pointer and invoke derived class behaviors without knowing the exact type.
- It is essential for **runtime flexibility** in object-oriented design.

Example:
```
class Shape {
public:
    virtual void draw() { std::cout << "Drawing shape\n"; }
};

class Circle : public Shape {
public:
    void draw() override { std::cout << "Drawing circle\n"; }
};

Shape* s = new Circle();
s->draw();  // Output: Drawing circle
```
Here, `draw()` behaves differently depending on the actual object (`Circle`), not the pointer type (`Shape*`).


---
#### **Pointers and Class Hierarchy**

Polymorphism relies heavily on **base class pointers or references** pointing to derived class objects.

Key points:
- Base class must have **virtual functions** to allow dynamic dispatch.
- Only pointers or references can provide runtime polymorphic behaviour; **objects themselves cannot**, due to object slicing.
    
**Example:**
```
Shape shapeObj;
Circle circleObj;

Shape* ptr = &circleObj;
ptr->draw();  // Calls Circle's draw() because draw() is virtual
```
`Shape shapeObj = circleObj;` would **slice** the object, keeping only the base portion.


---
#### **Dynamic Binding**

Dynamic binding (also called **late binding**) determines which function implementation to call at **runtime**.
- Achieved through **virtual functions** in C++.
- The compiler sets up a **vtable** (virtual table) for classes with virtual functions.
- This enables calling the correct overridden function depending on the actual object type.

**Example:**
```
Shape* ptr = new Circle();
ptr->draw();  // Runtime decides to call Circle::draw()
```


---
#### **Abstract Classes**

An **abstract class** cannot be instantiated and is used as a blueprint. It typically contains at least **one pure virtual function**.

**Syntax:**
```
class Shape {
public:
    virtual void draw() = 0;  // pure virtual function
};
```
- Derived classes **must implement** all pure virtual functions to be concrete.
- Abstract classes define an interface for polymorphism.

**Example:**
```
class Circle : public Shape {
public:
    void draw() override { std::cout << "Circle drawn\n"; }
};
```


---
#### **Dynamic Casting**

The **main purpose** of `dynamic_cast` is to let you:
	Safely call subclass-specific functions on a base class pointer or reference **at runtime**, but _only_ if the object actually _is_ that subclass.

`dynamic_cast` is a **runtime-checked type conversion** in C++ that’s specifically meant for **polymorphic types** (classes with at least one virtual function).

It allows you to safely:
- Convert a **base class pointer/reference** to a **derived class pointer/reference**,
- Or check if a cast is valid at runtime.

In other words:
> `dynamic_cast` asks the runtime, “Is this pointer actually pointing to an object of type X (or a subclass of X)?”

If yes → it performs the cast.  
If no → it safely returns `nullptr` (for pointers) or throws an exception (for references).

**Example:**
```
Shape* s = new Circle();
Circle* c = dynamic_cast<Circle*>(s);
if (c) c->draw();  // Safe to call
```
Useful when you have a heterogeneous collection of base pointers and need specific derived behaviour.


---
#### **Design Patterns**

Polymorphism is a core enabler for many **OOP design patterns**:
- **Factory Method**: Returns objects of base type, but actual type determined at runtime.
- **Observer**: Subscribers implement an interface; polymorphism allows calling `update()` without knowing concrete types.
- **Decorator**: Base type reference can point to dynamically wrapped objects.


---
#### **Encapsulating Behaviour**

Polymorphism allows encapsulating **variable behaviour** behind a common interface:
- Clients code against the **interface** rather than the concrete class.
- This allows extending behaviour without changing client code.

**Example:**
```
class Weapon {
public:
    virtual void attack() = 0;
};

class Sword : public Weapon {
public:
    void attack() override { std::cout << "Swing sword\n"; }
};

class Bow : public Weapon {
public:
    void attack() override { std::cout << "Shoot arrow\n"; }
};

void performAttack(Weapon* w) { w->attack(); }
```
`performAttack` doesn’t care if it’s a sword or bow — polymorphism handles the variation.


---
#### **Strategy Design Pattern**

The **Strategy Pattern** encapsulates algorithms or behaviors in **separate classes** and makes them interchangeable.
- Relies on polymorphism for flexibility.
- Avoids conditionals and tightly-coupled logic.

**Example:**
```
class FlyBehavior {
public:
    virtual void fly() = 0;
};

class FlyWithWings : public FlyBehavior {
public:
    void fly() override { std::cout << "Flying with wings\n"; }
};

class FlyNoWay : public FlyBehavior {
public:
    void fly() override { std::cout << "Cannot fly\n"; }
};

class Duck {
    FlyBehavior* flyBehavior;
public:
    Duck(FlyBehavior* fb) : flyBehavior(fb) {}
    void performFly() { flyBehavior->fly(); }
};
```

You can switch strategies at runtime:
```
Duck duck(new FlyWithWings());
duck.performFly();  // "Flying with wings"
```
Changing to `FlyNoWay` dynamically changes behavior without modifying `Duck`.


---
