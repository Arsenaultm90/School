Inheritance is an OOP principle that allows us to model the “is a” relationship among classes.

A superclass or parent class is a more general class.  
A subclass or a child class is a more specific class.


---
##### The Extends Keyword

When a class A extends from another class B:  
	public class A extends B {...}  
	
• A is a subclass of B  
• B is a superclass of A  
• Class A receives ALL public/protected attributes from class B  
• Class A receives ALL public/protected methods from class B  
• Constructors are not inherited, but the parent’s constructor is called from  
the child class (important!)  
• In Java, a class can only inherit from ONE other class.


---
##### The Equals Method

The $'=='$ operator compares if two variables refer to the same memory location.

The equals() method will compare the actual value of the strings, or more specifically the characters of the string, to check if they match.

```
String s1 = "hello"; 
String s2 = "hello"; 
String s3 = new String("hello"); 

System.out.println(s1 == s2); // true (same memory reference, string pool) 
System.out.println(s1 == s3); // false (different memory locations) 
System.out.println(s1.equals(s3)); // true (same character content)
```


---
##### Constructors In Inheritance

Constructors are not inherited!  
You can call a direct parent class’s constructor as follows, 

```
super(arguments);  
```


It must be the first line in the subclass’s constructor (important!)


---
##### Method Overriding

Method overriding allows us to overwrite the behaviour of a parent’s method.  

Override -> write parent class’s method in a child class with the same signature but different implementation.  

Can still call the direct parent-version of the method directly with  

```
super.methodName(arguments)
```



---
##### Final Modifier

A final variable (examples: Math.PI, Math.E):  
	• value cannot be changed once it is defined, used for constants  
	• must be defined in the initialization block  
	
A final method:  
	• cannot be overridden  
	• cannot be abstract  
	• allows you to guarantee its behaviour is identical across all subclasses  
	
A final class (examples: Math, Integer, Float, Double):  
	• cannot be extended  
	• cannot be abstract