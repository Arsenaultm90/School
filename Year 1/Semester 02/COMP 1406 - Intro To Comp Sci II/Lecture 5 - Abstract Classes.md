Data **abstraction** is the process of hiding certain details and showing only essential information to the user.  

Abstraction can be achieved with either **abstract classes** or interfaces.

The **abstract** keyword is a non-access modifier, used for classes and methods:

- **Abstract class:** is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).
  
- **Abstract method:** can only be used in an abstract class, and it does not have a body. The body is provided by the subclass (inherited from)


---
##### Abstract Methods

Note: an abstract class can have both :
	• concrete methods (regular methods that we have been writing so far)  
	• abstract methods → have the method signature but no body (no curly braces, no method implementation)

Example : 

```
public boolean deposit(double amount){//code}  
public abstract boolean withdraw(double amount);
```

Abstract methods MUST be overridden in all concrete subclasses.


---
##### Abstract vs Concrete Classes

**Abstract class:**  
	• cannot be instantiated, gives a framework for the child-classes.  
	• cannot be a final class.  
	• can contain all regular components such as constructors, variables, methods  
	(abstract/concrete, static, final etc.).  
	• is a valid reference data type 

**Concrete class:**  
	• can be instantiated.  
	• can have concrete methods only with other regular components.  
	• is also a valid reference data type.

