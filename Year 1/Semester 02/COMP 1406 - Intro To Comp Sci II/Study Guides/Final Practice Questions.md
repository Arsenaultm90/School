1. **Java is a ___ and ___ language.**

- **Independent** – Java is _platform-independent_ because of the Java Virtual Machine (JVM). You can write Java code once and run it anywhere that has a JVM (often referred to as “write once, run anywhere”).
    
- **Statically typed** – Java requires you to declare the type of variables at compile time. The type of a variable is known at compile time and cannot change.



2. **Which one is not one of the steps for creating an object?**

- "Implementation" refers to **defining how a class works**, usually by writing its methods or implementing an interface.
- It's part of **class design**, not **object creation**.


3. **The initialization of an object is the responsibility of its _____.**

The initialization of an object is the responsibility of its **constructors**.
- A **constructor** in Java is a special method that is **called automatically when an object is created**.
    
- It **initializes the object's state** (i.e., sets up its variables, performs setup tasks, etc.)



 4. **Local variables of a function are stored in the ____ memory.**
 
Local variables of a function are stored in the **stack** memory.
- **Stack memory** is used for:
    - Storing **local variables**
    - **Function call information** (like return addresses)
    - Memory is automatically allocated and deallocated when methods are called and return
        
- **Heap memory**, on the other hand, is used for:
    - Objects created with `new`
    - Global/static variables and dynamically allocated data that persist beyond a single function call



5. **A class having two methods with the same name but different arguments is an example of _______.**

An example of **method overloading**.
- **Method overloading** occurs when a class has multiple methods with the **same name** but **different arguments** (either in number, type, or both).
- The return type **does not** matter when overloading methods; only the method signature (name + parameters) counts



6. **Assume we are designing a Car class. We need to write a utility method that works for the Car class, i.e., not for any Car object. What modifier should we use for this method?**


**`static`** is the right modifier to use in this case.
- A **static method** belongs to the class itself rather than to any specific instance of the class (i.e., it works at the class level).
- Static methods can be called **without creating an instance** of the class



7. **Which of the following is NOT an advantage of proper encapsulation?**

Uses less memory when executed
Encapsulation helps with **maintaining integrity and abstraction**, but **it doesn't inherently reduce memory usage**. Hence, the answer is **"uses less memory when executed"**



 8. __________ helps deal with the complexity of a system by hiding unnecessary details.
 
**Abstraction** is the right answer.
- **Abstraction** is a key principle in object-oriented programming (OOP) that helps to **hide unnecessary details** and expose only the essential features of a system or object.
- It allows you to focus on what an object does **instead of how it does it**. By abstracting out implementation details, you make complex systems easier to understand and interact with.



9. **private, public, and protected are examples of ________.**

Access modifiers
- **Access modifiers** in Java (and many other programming languages) define the **visibility** or **accessibility** of classes, methods, and variables.
- They control **who** can access a class, method, or variable, and from where.

Common access modifiers:
**`private`**: The member is accessible only within the same class.
**`public`**: The member is accessible from any other class.
**`protected`**: The member is accessible within the same package and by subclasses (including those in different packages).
 **`default`** (no modifier): The member is accessible only within classes in the same package.



10. **This pair of keywords indicates that an attribute belongs to the class at a class-wide level and that it cannot be reassigned**

**`final static`** is the right answer.
- **`static`**: This keyword indicates that the attribute belongs to the class itself rather than to any specific instance of the class. It means the attribute is shared across all instances of the class.
- **`final`**: This keyword ensures that the attribute **cannot be reassigned** once it has been initialized. It makes the attribute **constant**.



11. **A class can access _______ (select all that apply).**

All public, private, and protected variables.
All protected variables of its parent class



12. **If A is a subclass of B, then which of the following is true:**

**Objects of type A can be stored in variables of type B** is the right answer.
In object-oriented programming, when **A is a subclass of B** (i.e., `A` **extends** `B`), **A** inherits the properties and behaviors of **B**. This means that **A** is a more specific version of **B**, and objects of type **A** can be treated as objects of type **B** due to inheritance.

This is known as **polymorphism**. Specifically, this behavior allows a variable of the superclass type (`B`) to reference an object of the subclass type (`A`).



13. **Assume you are working with two classes - Dog and Mammal. Which of the following logical hierarchies would make the most sense?**

Mammal is a superclass and Dog is a subclass

In the real world, a **Dog** is a type of **Mammal**. This follows the **"is-a"** relationship, which is key in object-oriented programming when defining class hierarchies.

- **Mammal** represents a more **general category** (a superclass).
- **Dog** is a more **specific type of mammal** (a subclass). A dog **is a** mammal, but not all mammals are dogs.



14. **Constructors are not inherited by a child class, but a parent's constructor can be called using the _ keyword.**

**`super`** is the right keyword.
- In Java (and many other object-oriented programming languages), **constructors are not inherited** by a subclass. This means that the child class does not automatically inherit the constructor of the parent class.
- However, a **child class can call the parent's constructor** explicitly using the **`super`** keyword. This is typically done to initialize the parent class part of the object when creating an instance of the child class.



Consider the following code. 
```
public class Parent { 
	int x; 
	
	public Parent(int x){ 
		this.x = x + x; 
	}
} 

public class Child extends Parent{ 
	public Child(int x){ 
		super(x); 
		this.x = x + 5; 
	} 
} 
```

What will be the output of this? 

```
Child c = new Child(2); 
System.out.println(c.x); 
Parent p = new Parent(2); 
System.out.println(p.x);
```

Output will be 7 and 4



15. **Which of the following is true about an abstract class?**

An **abstract class** in Java:
- **Cannot be instantiated directly** — you **cannot create an object** of an abstract class using `new`.
- **Can contain both abstract and non-abstract methods**.
- Is meant to be **extended by subclasses**, which must provide implementations for its abstract methods.



16. **An abstract subclass can implement inherited abstract methods.**

An **abstract subclass** **can implement** inherited abstract methods — but it's **not required to** implement all of them unless it's going to be a concrete class.



17. **To treat an object of type A as an object of type B, this must be true:**

**"A is a subclass of B"** is **correct** when it comes to treating an object of type A as an object of type B.

If **A is a subclass of B**, that means A **inherits** from B. So, A **is a B** (in the "is-a" relationship). This is what allows **upcasting** — treating a subclass as if it were an instance of its superclass.



18. **A class can extend from __ abstract class(es) and can implement __ interface(s).**

A class can extend from **one** abstract class and can implement **many** interface(s).
**Extending Classes (including abstract ones)**:
- Java only supports **single inheritance** with classes.
- So a class can **extend only one** superclass (whether abstract or not).

 **Implementing Interfaces**:
- Java supports **multiple inheritance** with interfaces.
- A class can implement **as many interfaces** as it wants.



19. **If A is the subclass of B and implements interface C, which of the following class declarations is valid?**

> **`class A extends B implements C`**

In Java, when a class:
- **Inherits** from another class (even an abstract one), use `**extends**`
- **Implements** an interface, use `**implements**`

And the order matters:
- **extends** must come first (only one class)
- **implements** comes after (can be multiple interfaces)



20. **The last-in first-out principle is associated with which ADT?**

The Stack



21. **To implement the queue ADT using a list for storage, which list implementation would be best?**

`LinkedList` allows **efficient removal from the front** of the list.



22. **Any List implementation may be used as the instance for a List interface variable. This is an example of _.**

Polymorphism



23. **If HashMap X stores keys of type String and values of type Double, then assuming X.get(Y) executes successfully, it will return a _.**

A Double



24. **NullPointerException is a type of checked exception and needs to be handled using try/catch blocks.**

False - It extends a runtime exception



24. **This is optionally used after a set of catch blocks and is always executed.**

Finally



25. **You must implement the Serializable interface if you want to read/write ___ from/to a file.**

Objects
If you want to **read/write objects** to/from a file in Java — meaning, you want to **serialize** and **deserialize** them — the class **must implement** the `Serializable` interface.



26. **Which of the following stream classes works with human-readable data?**

PrintWriter
**`PrintWriter`** is specifically designed for writing **human-readable data**. It can write characters, formatted text, and strings to a file or console.

It handles text output (i.e., character-based data), which is typically more **human-readable** than binary data.


```
import java.io.*;

public class Example {
    public static void main(String[] args) throws IOException {
        PrintWriter writer = new PrintWriter("output.txt");
        writer.println("This is human-readable text.");
        writer.close();
    }
}
```



 27. **Which one is the disadvantage of recursive methods?**

More Memory Overhead
- **Each recursive call** stores its state (local variables, return address) on the stack.
- **Deep recursion** can lead to high memory usage since the call stack grows with each recursive call.



28. **A node in a doubly linked list that represents the end of the list is called the __.**

The Tail Node
The **tail** node is the actual last node in the list containing the data.



29. **In the typical recursive implementation of the Fibonacci sequence, where 𝑓𝑖𝑏(𝑛) = 𝑓𝑖𝑏(𝑛 − 1) + 𝑓𝑖𝑏(𝑛 − 2) 𝑓𝑜𝑟 𝑛 ≥ 2, how many recursive calls are made (excluding the initial call) when calculating fib(4)?**

8 Calls
```
fib(4)
│
├── fib(3)
│   ├── fib(2)
│   │   ├── fib(1) (base case)
│   │   └── fib(0) (base case)
│   └── fib(1) (base case)
└── fib(2)
    ├── fib(1) (base case)
    └── fib(0) (base case)
```



30. **Which of the following is an inorder traversal for this binary tree?**
Inorder (Left, Root, Right)
Preorder(Root, Left, Right)
Postorder (Left, Right, Root)
![[Pasted image 20250413124615.png]]

SUQPRVT


