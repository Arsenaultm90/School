#### What is Software Engineering?

**Software Engineering (SE)** is the systematic approach to designing, developing, testing, and maintaining software.

**Key points:**
- Focuses on **quality, maintainability, and efficiency**.
- Uses **engineering principles** rather than ad-hoc coding.
- Involves stages: **requirements → design → implementation → testing → maintenance**.

**Example:** Building a banking system requires clear planning, modular design, testing, and long-term maintainability—this is software engineering.



---
#### Low-Level Design (LLD)

**LLD** deals with the **internal design of modules/classes** in detail.
- Specifies how **each component works** internally.
- Focuses on **data structures, algorithms, class design, and interfaces**.

**Encapsulation**
- Hiding internal details of a class and exposing only necessary functionality.
- Achieved via **private/protected members** and **public methods**.
```
class BankAccount {
private:
    double balance; // hidden
public:
    void deposit(double amount) { balance += amount; }
    double getBalance() { return balance; }
};
```

**Abstraction**
- Hiding **complex implementation details** while exposing **what the object does**.
- Focuses on **behavior, not implementation**.
```
class Shape {
public:
    virtual double area() = 0; // abstract method
};
```

**Principle of Least Priviledge**
- Each module/class/function should **only have access to what it needs**.
- Reduces **bugs, security risks, and unintended side-effects**.
```
class User {
private:
    std::string password; // only accessible inside class
};
```



---
#### High-Level Design (HLD)

**HLD** deals with the **overall system architecture**.
- Defines **modules, components, data flow, and system interfaces**.
- Focuses on **how components interact**, not the internal logic.

**Example:**
- Designing an e-commerce system: HLD would specify modules like **User Management, Product Catalog, Payment Processing**, and their interactions.


---
#### Workflow

**Workflow** defines the **process of software development**.
- Common models: **Waterfall, Agile, Scrum, DevOps**.
- Workflow stages:
    1. Requirements gathering
    2. Design (HLD & LLD)
    3. Implementation
    4. Testing
    5. Deployment
    6. Maintenance

**Example:** Agile workflow: short sprints, frequent releases, continuous feedback.


---
#### Testing

Testing ensures **software works correctly and reliably**.

**Unit Testing**
- Tests **individual components/classes/functions** in isolation.
- Example: Testing a `deposit()` function in `BankAccount` class.

**Integration Testing**
- Tests **interaction between modules**.
- Example: Checking if `Payment Module` correctly updates `Order Module`.

**System Testing**
- Tests the **entire system** end-to-end.
- Example: Simulating a complete e-commerce transaction from login → cart → payment → receipt.


---
#### Real-World Examples

**The Art of Unix Programming**
- Book emphasizing **simplicity, modularity, and composability** in Unix systems.
- Encourages **small, reusable tools** that work together.

**Amazon Web Services (AWS)**
- Real-world cloud platform example.
- Shows **scalable design, modular services, distributed architecture**, and **high reliability**.

**Google’s How to Design a Good API**
- Guidelines for creating **clean, intuitive, and maintainable APIs**.
- Focuses on **consistency, simplicity, error handling, and backward compatibility**.


---
#### Software Engineering Flow Diagram

```
      +-------------------+
      |   Requirements    |
      +-------------------+
               |
               v
      +-------------------+
      |  High-Level Design|  
      +-------------------+
      Defines system modules, architecture, data flow
      
               |
               v
      +-------------------+
      |  Low-Level Design |  
      |  - Encapsulation  |
      |  - Abstraction    |
      |  - Least Privilege|
      +-------------------+
      Defines classes, functions, data structures
      
               |
               v
      +-------------------+
      |    Implementation | 
      +-------------------+
      Actual coding of classes/modules
               |
               v
      +-------------------+
      |      Testing      |  
      |  - Unit Testing   |
      |  - Integration    |
      |  - System Testing |
      +-------------------+
      Verify software correctness
      
               |
               v
      +-------------------+
      |    Deployment &   |
      |    Maintenance    |
      +-------------------+

```

1. **Requirements:** Gather what the system should do.
    
2. **High-Level Design:** Identify modules/components and their interactions.
    
3. **Low-Level Design:** Specify internal details of each module (classes, methods, data).
    - **Encapsulation:** Keep data private
    - **Abstraction:** Show only necessary behaviors
    - **Least Privilege:** Give minimal access rights
        
4. **Implementation:** Write the actual code.
    
5. **Testing:** Verify functionality at different levels.
    
6. **Deployment & Maintenance:** Release software and fix issues over time.