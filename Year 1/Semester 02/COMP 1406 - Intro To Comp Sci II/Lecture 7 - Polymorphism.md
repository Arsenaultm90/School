Polymorphism allows objects of different classes to be treated as objects of a common superclass. It enables **one interface, multiple implementations**, making code more flexible and reusable.

**Compile time polymorphism (early binding)**  
	Overloaded method.  
	Decision which overloaded method to use is taken at compile time.  

**Runtime polymorphism (late binding)**  
	Overridden method. Subclass defines the same superclass method (same method name, same parameters).  
	Decisions are made by the JVM during runtime.



---
##### Typecasting Primitives

**Explicit Typecasting**

```
char a = (char)65; // a is ‘A’  
double d = 3.14; // d is 3.14  
int i = (int)d; // i is 3
```


**Implicit Typecasting**

```
double x = 4; // x is 4.0
```


**Invalid Typecasting**

```
double h = (double)“Hey!”; //ERROR!
```



---
##### Typecasting Objects

```
Pet pet1 = new Cat();  
Animal animal1 = new Dog();  
Pet pet2 = new Poodle();  
Dog dog1 = new Poodle();
```

**pet1** refers to a Cat object but the Cat object does not get changed, only gets represented as a Pet. This casting is checked during compile time.



---
##### Upcasting

An object of type A can be treated as an object of type B if  

1. A is a descendant of B  
	(i.e., B is above A in the class hierarchy)  
	B b1 = new A();  

2. A implements the interface B  
	B b2 = new A();  

3. An object of type A was initially cast to type B and now it is being cast back to type A  
(i.e., A is being cast back to its original type)  
	B b = new A();  
	A a = (A)b;


---
##### Polymorphism With Interfaces

Polymorphism works with interfaces: if a class implements an interface, an object of that class can be typecast to a variable of that interface type.

![[Screenshot 2025-02-04 at 8.03.53 AM.png|500]]

• Poodle can be treated as a Poodle, a Dog, a Pet, an Animal, an Object, and a Trainable  
• Wolf can be treated as a Wolf, an Animal, and an Object


---
##### Single vs. Double Dispatch in Polymorphism

Polymorphism allows dynamic method resolution at runtime. **Single and double dispatching** describe **how many factors determine the method that gets called**.

1. **Single Dispatch (Java’s Default Behavior)**
	- The method to be executed is determined **only by the runtime type of the calling object**.
	- The parameters do **not** influence method selection at runtime.
	- Java supports **only single dispatch natively**.


```
class Animal { 
	void makeSound() { 
		System.out.println("Animal makes a sound"); 
	} 
} 

class Dog extends Animal { 
	@Override void makeSound() { 
		System.out.println("Bark!"); 
	} 
} 

public class Main { 
	public static void main(String[] args) { 
		Animal a = new Dog(); // Polymorphism (reference type is Animal, object type is Dog) 
		a.makeSound(); // Output: "Bark!" (Dog's method is called) 
	} 
}
```

- `a` is declared as `Animal`, but the **actual object is `Dog`**.
- Java **dispatches the method based on the object type (`Dog`)**, ignoring the reference type (`Animal`).



1. **Double Dispatch (Requires Workaround in Java)**
	- The method execution is based on **both** the runtime type of the calling object **and** the runtime type of its parameters.
	- Java does **not** support this natively, but **Visitor Pattern** is a common way to implement it.

