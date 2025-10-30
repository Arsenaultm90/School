####  **Overview**

A **linked list** is a **linear data structure** made of **nodes**, where each node stores:
- **Data**
- A **pointer to the next node** (and sometimes to the previous node, in a doubly linked list)

Unlike arrays, linked lists:
- Don’t use contiguous memory.
- Allow **efficient insertions/deletions** anywhere in the list.
- Have **slower access time** (you must traverse from the head to reach an element).

**Structure :**
```
struct Node {
    int data;
    Node* next;
};
```

##### Encapsulation and Access
Encapsulation means keeping the list’s **internal structure hidden** from the user.

Instead of letting the user directly manipulate nodes and pointers,  
we define a `LinkedList` **class** that provides a **public interface** (e.g., `insert`, `remove`, `display`)  
while keeping the actual implementation details **private**.


##### Abstract Interfaces
Sometimes you want **different types of lists** (singly, doubly, circular)  
but want them to share a common **interface** — e.g., all support `insert()`, `remove()`, and `display()`.


##### Separation of Data and Containers
This is a key design concept in modern C++.

You want to **separate the “data” being stored** from the **container structure** that holds it.  
The linked list should be a **template class**, so it can store _any_ data type.


##### Memory Management
Linked lists rely **heavily on dynamic memory** (`new` and `delete`).
That means you must manage:
- Allocation (`new Node`)
- Deallocation (`delete Node`)
- Avoiding leaks and dangling pointers

**Proper management techniques:**
- **Destructor** cleans up all nodes.
- **Copy constructor** and **assignment operator** must perform **deep copies**, not shallow ones.
- Or, better: disable copying entirely or use smart pointers.


**Summary :**

| Concept                             | Description                                 | Example Benefit                      |
| ----------------------------------- | ------------------------------------------- | ------------------------------------ |
| **Encapsulation & Access**          | Hide nodes/pointers, expose clean interface | Prevents corruption                  |
| **Abstract Interfaces**             | Define `IList` base class                   | Enables polymorphism                 |
| **Separation of Data & Containers** | Use templates to store any data             | Reusable container                   |
| **Memory Management**               | Manage dynamic memory safely                | Prevent leaks and undefined behavior |
