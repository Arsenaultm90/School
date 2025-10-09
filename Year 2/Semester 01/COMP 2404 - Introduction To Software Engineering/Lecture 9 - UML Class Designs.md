#### Documentation

**Software Development Lifecycle**
1. Requirements Analysis
2. Design
3. Implementation
4. Testing

**Requirements Analysis**
- Functional requirements  
	- Specifies what the system will do  
- Non-functional requirements  
	- User-visible constraints on the system  
- Use cases  
	- Model the interactions between the user and the system 
	- (particularly useful)  
- High-level object model  
	- A model of the interactions of the objects in your application  
	- Major entity, boundary and control objects  
- Dynamic model  
	- System behaviour over time.

**Design**
- Subsystem decomposition  
	- Specification of the high-level subsystems  
- Detailed object model  
	- Low level objects required to implement the system interfaces

**Implementation**
- Program comments, intelligent naming conventions  
- Tutorials

**Testing**
- Test plan  
- Test cases


---
#### Unified Modelling Language (UML)

A **UML (Unified Modeling Language) class diagram** is a static diagram that represents the **classes** in a system, their **attributes**, **methods**, and **relationships**. It’s one of the most common UML diagrams for object-oriented design.

**Elements of a Class Diagram**
1. **Class** – Represented by a rectangle divided into three sections:
```
+------------------+
| ClassName        |   <- Name
+------------------+
| attribute1        |
| attribute2        |   <- Attributes (variables)
+------------------+
| method1()         |
| method2()         |   <- Methods (functions)
+------------------+
```

Abstract classes and methods are shown in italics  
Static members are underlined

2. **Attributes** – Properties of the class. Visibility symbols:
    - `+` public
    - `-` private
    - `#` protected
	**Syntax:**  
		Start with access modifier -, #, +
		Followed by the attribute name  
		Followed by : followed by type
		Ex: `-fooBar:string`

3. **Methods** – Functions or operations of the class. Same visibility symbols as attributes.
	**Syntax:**  
		Access modifier -, #, +  
		Followed by operation name  
		Followed by (parameters) (separated by commas):  
			in, out, or inout parameter  
			parameter name : type  
		Followed by : followed by return type  
		May be blank if returns void
		Ex: 
```
+ makeLine(inout line:Line)  
+ playLine(in line: Line)  
+ addPlayer(in player:Player): bool  
+ removePlayer(in name: string, out player:Player): boo
```


4. **Relationships** – Connect classes to show their interactions:
    - **Association** – Simple relationship between classes (solid line).
    - **Multiplicity** – Shows how many instances relate (e.g., 1..*, 0..1).
    - **Aggregation** – “Has-a” relationship, represented by a hollow diamond.
    - **Composition** – Strong “Has-a” relationship, represented by a filled diamond.
    - **Inheritance (Generalization)** – “Is-a” relationship, represented by a solid line with a hollow triangle pointing to the parent.
    - **Dependency** – A class depends on another, shown with a dashed arrow.
        
5. **Interfaces** – Abstract classes or methods, usually with a dashed line showing implementation.


