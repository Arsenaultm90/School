##### Class vs Object

**Class :**
	The definition/template of an object (type),  specifying its properties and behaviour.Classes are like cookie-cutters (e.g., Person class).

**Object/instance :** 
	A specific copy of a class. The objects of the Person class can be jane, john, farah.


**Two aspects make up an object :**  
1. States (attributes/instance variables)  
2. Behaviour (methods)


---
##### Naming Conventions

**Classes :** nouns, first letter of each word capitalized  
	Examples: Car, BankAccount, Student, GradStudent  

**Methods :** verbs, first word in lowercase, first letter of other words capitalized  
	Examples: drive, driveCar, addAccount, incrementCounter  

**Variables :** short, meaningful, mnemonic names with consistent capitalization  
	Examples: monthlyFee, studentList, accountNumber


---
##### Java Memory Model
All primitives and objects are stored in computer’s memory during runtime.  
JVM allocates 4 logical areas/types of memory space for a Java program.

![[Screenshot 2025-01-16 at 11.12.06 AM.png]]

1. Static area – global and static variables  
2. Heap area – objects  
3. Stack area – local variables  
4. Free memory – not being currently used by your program

**Primitives in Memory Visualization**
Each primitive value is stored in a block of memory.  
The block size depends on the number of bytes taken by each primitive type

**Objects in Memory Visualization**
Objects (non-primitives) are ‘pointed’ or ‘referred’ to using memory addresses.  
A memory address can be represented with a fixed amount of space (e.g., 32 bits or  
64 bits – depends on the machine size)

![[Screenshot 2025-01-16 at 11.15.46 AM.png]]


---
##### Constructors

Used when creating instances of a class.  
Responsible for initializing all attributes.  
	Example: modify the Address class to have a default constructor that initializes all attributes to default values.


---
##### Printing Objects Using toString()

What happens when we print our own objects? The toString() method is called automatically to convert an object to a String before printing it.  

Default toString() is included – prints memory address, we can change it to customize the look of our objects by creating a String.

![[Screenshot 2025-01-16 at 11.18.44 AM.png]]


---
##### Method Overloading

Method Overloading: having more than one method having the same name but different signatures in the same class.

A method signature consists of:  
1. The name of the method  
2. The number/type/order of arguments (not the return type)


---
##### Instance vs Static

**Static Methods**
The keyword static is a modifier.  
It indicates something (variable/method) belongs to the class at a class-level (not to individual  
objects)  

```
public static double convertUSDtoCAD(double usd){  
...  
}
```

Static methods are typically utility methods. Java’s Math class has many static methods.  
	Examples: Math.sqrt(), Math.max(), Math.pow()

It cannot access/modify any instance (non-static) variables.  

```
String name;  

public static void changeName(){  
	name = "nothing"; //Error  
}
```


**Static Variables**
Static variables track class-wide state.  
A single copy for the entire class.  
Must be initialized when defined.  

```
public class Person { 

	String name;  
	Address address;  
	
	static boolean isHappy = true; // all person objects are happy  
	}
```


**The Final Modifier**
Final is a modifier used to declare constants (ALLCAP).  
Final variables cannot be re-assigned later in the code.  

```
public class Bank {  
	final int MAX_ACCOUNTS = 2;
	  
	public Bank (){  
		// MAX_ACCOUNTS = 5;  
		// error - cannot reassign a value to a final variable  
	}  
}
```

A final variable (examples: Math.PI, Math.E):  
	Value cannot be changed once it is defined, is used for constant  
	Must be defined in the initialization block  

A final method:  
	Cannot be overridden  
	Cannot be abstract  
	Allows you to guarantee its behaviour is identical across all subclasses  
	
A final class (examples: Math, Integer, Float, Double):  
	Cannot be extended  
	Cannot be abstract

