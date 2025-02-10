Inheritance allows similar classes to share common attributes and behaviour.  

Interface allows non-similar classes to exhibit common behaviour without being in the same logical hierarchy.

An interface defines a contract for additional class behaviour, i.e., a group of ‘implicitly abstract’ methods.

A class can implement as MANY interfaces as necessary.

**Example :** 
Person, Building, and Car are all things that we might insure, but they do not share common class-specific states/behaviours.

**Note:** any class that implements an interface must implement all the methods outlined in that interface.

```
public interface Insurable{  

//method definitions with no particular implementation  
public int getPolicyNumber();  
public double getCoverageAmount();  
}

public class Car implements Insurable { ...}  
public class Person implements Insurable { ...}  
public class Building implements Insurable { ...}
```


If a class A implements an interface B :
	• It will not compile until ALL methods specified in B are implemented in class A  
	• All subclasses of A also implement B



---
##### Summary

Interfaces can  
	• contain public and implicitly abstract method declaration and  
	• extend any number of other interfaces.  

• If a class implements a given interface, all interface methods must exist within that class.  
• Interfaces is a valid reference data type (can have variables of this type).