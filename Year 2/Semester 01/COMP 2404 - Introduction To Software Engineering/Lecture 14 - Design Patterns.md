**Design Patterns** are proven, reusable solutions to common software design problems.  
They aren’t code templates, but _conceptual blueprints_ for structuring your classes and objects.

They’re often grouped into **three major categories:**

|Category|Purpose|Example Patterns|
|---|---|---|
|**Creational**|How objects are _created_|Factory, Singleton, Builder, Prototype|
|**Structural**|How objects are _organized or composed_|Facade, Adapter, Composite, Decorator|
|**Behavioral**|How objects _communicate and interact_|Strategy, Observer, Command, State|

Think of them like:
- **Creational** → “Who makes it?”
- **Structural** → “How are they connected?”
- **Behavioural** → “How do they talk to each other?”


---
#### **Facade Pattern (Structural)**

##### Purpose
Provides a **simplified interface** to a complex subsystem.  
You use it when you want to **hide complexity** behind a single, easy-to-use class.

##### Analogy
A _facade_ on a building hides all the wiring and pipes behind a clean, simple front.  
Similarly, the pattern hides the inner workings of a complex system.

Example:
```
// Complex subsystem
class CPU {
public:
    void freeze() { cout << "CPU frozen\n"; }
    void jump(long position) { cout << "Jumping to " << position << "\n"; }
    void execute() { cout << "Executing instructions\n"; }
};

class Memory {
public:
    void load(long position, string data) { cout << "Loading data into memory\n"; }
};

class HardDrive {
public:
    string read(long lba, int size) { return "Boot data"; }
};

// Facade
class ComputerFacade {
private:
    CPU cpu;
    Memory memory;
    HardDrive hardDrive;
public:
    void startComputer() {
        cpu.freeze();
        memory.load(0, hardDrive.read(0, 1024));
        cpu.jump(0);
        cpu.execute();
    }
};

// Client
int main() {
    ComputerFacade computer;
    computer.startComputer(); // Simple interface!
}
```
The client only calls one method (`startComputer()`), even though the system does several things internally.


---
## **Observer Pattern (Behavioural)**

**One object (the Subject) maintains a list of observers and automatically notifies them when its state changes.**

It’s a way to design a **publish/subscribe** system where:
- The **Subject** publishes events.
- **Observers** subscribe to receive those events.

It lets you avoid **hard-coded dependencies**.

Without Observer:
- Object A must know _exactly_ which objects it should update.
- This creates tight coupling.

With Observer:
- Object A (“subject”) doesn’t know who the observers are.
- Observers register themselves.
- The subject just says: “Hey, something changed — notify everyone!”

##### Analogy
Think of a **YouTube channel**:
- The **channel** is the _Subject_.
- The **subscribers** are _Observers_.
- When the channel uploads a new video, all subscribers get notified.

Example:
```
#include <vector>
#include <iostream>
using namespace std;

class Observer {
public:
    virtual void update(string message) = 0;
};

class Subject {
    vector<Observer*> observers;
public:
    void attach(Observer* o) { observers.push_back(o); }
    void notify(string message) {
        for (auto o : observers)
            o->update(message);
    }
};

class Subscriber : public Observer {
    string name;
public:
    Subscriber(string n) : name(n) {}
    void update(string message) override {
        cout << name << " received update: " << message << endl;
    }
};

// Client
int main() {
    Subject channel;
    Subscriber s1("Alice"), s2("Bob");
    channel.attach(&s1);
    channel.attach(&s2);
    channel.notify("New video uploaded!");
}
```

Output:
```
Alice received update: New video uploaded!
Bob received update: New video uploaded!
```


---
## **Factory Pattern (Creational)**

##### Purpose
Encapsulates object creation so that code using those objects doesn’t depend on concrete class names. The factory creates an object of a derived class and returns it as a pointer/reference to the base class.

This improves **modularity** and **flexibility**.

##### Analogy
A **factory** makes products based on a request — you don’t need to know _how_ they’re made.

Example:
```
class Shape {
public:
    virtual void draw() = 0;
    virtual ~Shape() = default;
};

class Circle : public Shape {
public:
    void draw() override { cout << "Drawing Circle\n"; }
};

class Square : public Shape {
public:
    void draw() override { cout << "Drawing Square\n"; }
};

// Factory
class ShapeFactory {
public:
    static Shape* createShape(string type) {
        if (type == "circle") return new Circle();
        else if (type == "square") return new Square();
        else return nullptr;
    }
};

// Client
int main() {
    Shape* shape = ShapeFactory::createShape("circle");
    shape->draw();
    delete shape;
}
```
The client doesn’t depend on the concrete class — only on the factory and base interface.


---
#### **Strategy Design Pattern (Behavioural)**

##### Purpose
Defines a **family of algorithms**, encapsulates each one, and makes them interchangeable at runtime.

This allows you to change _how_ an object behaves without modifying its class.

##### Analogy
Imagine a game character that can switch weapons:
- The **character** is fixed.
- The **weapon** (behaviour) can change dynamically.

Example:
```
class AttackStrategy {
public:
    virtual void attack() = 0;
    virtual ~AttackStrategy() = default;
};

class SwordAttack : public AttackStrategy {
public:
    void attack() override { cout << "Swinging sword!\n"; }
};

class BowAttack : public AttackStrategy {
public:
    void attack() override { cout << "Shooting arrow!\n"; }
};

class Character {
    AttackStrategy* strategy;
public:
    Character(AttackStrategy* s) : strategy(s) {}
    void setStrategy(AttackStrategy* s) { strategy = s; }
    void performAttack() { strategy->attack(); }
};

// Client
int main() {
    SwordAttack sword;
    BowAttack bow;

    Character hero(&sword);
    hero.performAttack(); // "Swinging sword!"

    hero.setStrategy(&bow);
    hero.performAttack(); // "Shooting arrow!"
}
```
The `Character` stays the same — only the _strategy_ changes.

##### Key Advantages
- Eliminates large conditional statements.
- Enables runtime flexibility.
- Promotes composition over inheritance.


---
#### **Anti-Patterns**

##### Overview
An **anti-pattern** is a “bad” design solution that seems to work but leads to problems later — like poor maintainability, tight coupling, or code duplication.

|Anti-pattern|Description|Why It’s Bad|
|---|---|---|
|**God Object**|One class does everything|Breaks modularity|
|**Spaghetti Code**|No structure, tangled logic|Hard to debug or test|
|**Copy-Paste Programming**|Duplicated code blocks|Inconsistent fixes, maintenance nightmare|
|**Golden Hammer**|Using one tool/pattern for every problem|Misuse of design patterns|
|**Premature Optimization**|Optimizing before measuring|Makes code complex and inflexible|

Good patterns → reuse proven solutions.  
Anti-patterns → reuse proven _mistakes_.


---
#### **Summary Table**

| Pattern           | Type        | Purpose                                             |
| ----------------- | ----------- | --------------------------------------------------- |
| **Facade**        | Structural  | Simplify a complex system behind a single interface |
| **Observer**      | Behavioural | Notify multiple objects of changes automatically    |
| **Factory**       | Creational  | Create objects without specifying their exact class |
| **Strategy**      | Behavioural | Switch algorithms or behaviors at runtime           |
| **Anti-patterns** | —           | Common bad designs to avoid                         |
