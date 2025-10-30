#### **Overview**

**Encapsulation** is one of the four fundamental principles of object-oriented programming (OOP), alongside inheritance, polymorphism, and abstraction.

It means **bundling data (variables) and methods (functions) that operate on that data into a single unit (class)**, and **restricting direct access** to some of the object’s components to protect its integrity.

##### Why Encapsulation?
- Prevents external code from corrupting the internal state.
- Allows internal changes without affecting external code (good maintainability).
- Provides a controlled interface (via getters/setters or public methods).

Example :
```
class BankAccount {
private:
    double balance;  // Encapsulated data

public:
    BankAccount(double initialBalance) {
        if (initialBalance >= 0)
            balance = initialBalance;
        else
            balance = 0;
    }

    void deposit(double amount) {
        if (amount > 0)
            balance += amount;
    }

    double getBalance() const {  // Controlled access
        return balance;
    }
};
```
Here, `balance` is **private**, meaning code outside the class can’t modify it directly, only through `deposit()` and `getBalance()`.



---
#### **Composition (Has-a Relationship)**

Encapsulation also extends to **composition**, where one class **contains objects of another class**.

It’s called a **“has-a”** relationship.

Example :
```
class Engine {
public:
    void start() { std::cout << "Engine started\n"; }
};

class Car {
private:
    Engine engine;  // Composition: Car has an Engine

public:
    void startCar() {
        engine.start();  // Using Engine within Car
        std::cout << "Car started\n";
    }
};
```
- `Car` encapsulates `Engine` as a private member.
- Outside code doesn’t directly handle the `Engine`; it goes through the `Car` interface.

**Benefit:** Maintains encapsulation by hiding implementation details of the components inside a class.


---
#### **Constants (Const)**

Constants reinforce encapsulation by ensuring **data or methods cannot be changed** unintentionally.

Example :
```
class Circle {
private:
    const double PI = 3.14159;  // Constant member
    double radius;

public:
    Circle(double r) : radius(r) {}

    double area() const {  // const method: won’t modify any members
        return PI * radius * radius;
    }
};
```
- `const` variables can’t be modified after initialization.
- `const` member functions guarantee they won’t modify the object’s data. Crucial for encapsulation, since it allows safe access.


---
#### **Friendship**

A `friend` allows **specific external functions or classes** to access private/protected members, but **breaks encapsulation slightly** by design.

Used carefully when:
- Two classes need tight cooperation.
- Certain helper functions require access to internals.

Example :
```
class Box {
private:
    double width;

public:
    Box(double w) : width(w) {}

    friend void printWidth(const Box& b);  // Friend function
};

void printWidth(const Box& b) {
    std::cout << "Width: " << b.width << '\n';  // Accessing private data
}
```
- `printWidth()` is not a member, but it can access private `width` because it’s declared a **friend**.
- Similarly, an entire **class** can be made a friend.

Use friendship **sparingly**, as it bypasses normal encapsulation rules.


---
#### **Static Member Classes**

`static` members belong to the **class itself**, not to individual objects.  

This is useful for:
- Keeping shared data across all instances.
- Implementing counters, configuration values, or utility functions.

Example :
```
class Student {
private:
    static int studentCount;  // Shared among all objects
    std::string name;

public:
    Student(std::string n) : name(n) {
        studentCount++;
    }

    static int getStudentCount() {  // Can access only static members
        return studentCount;
    }
};

// Definition of static variable
int Student::studentCount = 0;
```
- All instances share one copy of `studentCount`.
- `static` functions don’t have access to `this` because they aren’t tied to an object.

Useful for encapsulating **class-wide state** or functionality.



---
#### Principle Of Least Privilege

This is a security principle (not just OOP) stating that a user, program, or object should have only the minimum privileges necessary to perform its task.
In programming, it often applies to access control, method visibility, and resource permissions.

**Purpose:**
- Reduces the risk of **accidental or malicious misuse** of data or functionality.
- Limits the impact of bugs or attacks.



---
#### **Summary**

|Concept|Purpose|Example Use|Effect on Encapsulation|
|---|---|---|---|
|**Encapsulation**|Hide internal data|Private data with getters/setters|Strengthens|
|**Composition**|Combine smaller objects|`Car` has an `Engine`|Strengthens|
|**Constants**|Prevent unwanted modification|`const double PI`|Strengthens|
|**Friendship**|Grant selective access|`friend class Logger`|Weakens (if overused)|
|**Static Members**|Share data among all objects|Object counters|Neutral (depends on design)|
