**Inheritance** allows one class (**derived class**) to acquire the properties and behaviors of another (**base class**).

**Basic Syntax :**
```
class Base {
public:
    void greet() { std::cout << "Hello from Base\n"; }
};

class Derived : public Base {
public:
    void greetDerived() { std::cout << "Hello from Derived\n"; }
};


Derived d;
d.greet();         // inherited from Base
d.greetDerived();  // defined in Derived

```

**Purpose:**
- Promotes **code reuse**
- Supports **hierarchical relationships** (e.g., Animal → Dog → Bulldog)
- Enables **polymorphism**


---
#### **Memory Layout**

Every derived object contains a **base class subobject** inside it.

Example :
```
class Base {
    int a;
};

class Derived : public Base {
    int b;
};

The memory layout (simplified) looks like this:
+----------------+
| Base::a        |
+----------------+
| Derived::b     |
+----------------+
```

Important points:
- The **base class part** exists _inside_ the derived object.
- A pointer/reference to `Derived` can be **upcast** to `Base` safely:
```
Derived d;
Base* b = &d;  // ok
```
- `sizeof(Derived)` ≥ `sizeof(Base)` (because it contains everything Base has + more)

If virtual functions exist, there’s also a **vtable pointer** (for dynamic dispatch), typically stored at the start of the object.


---
#### **Member Access**

Inheritance respects **access specifiers** (`public`, `protected`, `private`) in two ways.

**(A) Inside the Base class:**

| Member      | Accessible in Derived? | Accessible Outside? |
| ----------- | ---------------------- | ------------------- |
| `public`    | Yes                    | Yes                 |
| `protected` | Yes                    | No                  |
| `private`   | No                     | No                  |

**(B) The inheritance type modifies how base members appear in the derived class:**

|Inheritance Type|Base’s `public` becomes|Base’s `protected` becomes|Use Case|
|---|---|---|---|
|`public`|public|protected|Normal “is-a” relationships|
|`protected`|protected|protected|Internal inheritance|
|`private`|private|private|Implementation reuse only|

**Example :**
```
class Base {
public: int pub;
protected: int prot;
private: int priv;
};

class Derived : public Base {
    void f() {
        pub = 1;   // OK
        prot = 2;  // OK
        // priv = 3; Not accessible
    }
};
```


---
#### **Constructors and Destructors**

**Key Rules:**
- The **base class constructor** always runs **before** the derived class constructor.
- The **base class destructor** runs **after** the derived class destructor.

Example :
```
class Base {
public:
    Base() { std::cout << "Base constructor\n"; }
    ~Base() { std::cout << "Base destructor\n"; }
};

class Derived : public Base {
public:
    Derived() { std::cout << "Derived constructor\n"; }
    ~Derived() { std::cout << "Derived destructor\n"; }
};

int main() {
    Derived d;
}
```

Output :
```
Base constructor
Derived constructor
Derived destructor
Base destructor
```

Construction goes top-down; destruction goes bottom-up.


---
#### **Member Functions and Overriding**

**(a) Function Overriding**
A derived class can **redefine** a base function.
```
class Base {
public:
    virtual void speak() { std::cout << "Base speaking\n"; }
};

class Derived : public Base {
public:
    void speak() override { std::cout << "Derived speaking\n"; }
};
```
- `virtual` allows **runtime polymorphism**
- `override` ensures the function really overrides a virtual one

**(b) Function Hiding**
If you don’t use `virtual`, you get **function hiding** instead:
```
class Base { public: void speak() { std::cout << "Base\n"; } };

class Derived : public Base { public: void speak() { std::cout << "Derived\n"; } };
```

Then:
```
Base* b = new Derived();
b->speak();  // prints "Base" (no polymorphism)
```


---
#### **Types of Inheritance**

|Type|Description|Example|
|---|---|---|
|**Single**|One base → one derived|`class Dog : public Animal`|
|**Multilevel**|Chain of inheritance|`Animal → Mammal → Dog`|
|**Hierarchical**|One base → many derived|`Animal → Dog`, `Animal → Cat`|
|**Multiple**|One derived inherits from many bases|`class Amphibious : public Car, public Boat`|


---
#### **Multiple Inheritance**

A derived class can inherit from **more than one base class**:
```
class Printable { public: void print() { std::cout << "Printable\n"; } };
class Loggable { public: void log() { std::cout << "Loggable\n"; } };

class Report : public Printable, public Loggable { };
```


Then:
```
Report r;
r.print();
r.log();
```
Both interfaces combined.


---
#### **Summary**

|Concept|Description|Key Takeaway|
|---|---|---|
|**Overview**|Derived class reuses base functionality|Promotes reuse|
|**Memory Layout**|Derived object contains base subobject|Base part stored first|
|**Member Access**|Public/protected/private rules apply|Controls visibility|
|**Constructors/Destructors**|Base built first, destroyed last|Ensures proper order|
|**Member Functions**|Can override or hide base versions|Enables polymorphism|
|**Types of Inheritance**|Single, multilevel, hierarchical, multiple|Models relationships|
|**Multiple Inheritance**|Combine multiple bases; use virtual inheritance to avoid ambiguity|Powerful but tricky|
