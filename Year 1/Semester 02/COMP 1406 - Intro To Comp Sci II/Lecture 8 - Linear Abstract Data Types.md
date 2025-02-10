Abstract Data Type (ADT) is a model that specifies a set of operations (e.g., store, access, modify, remove) on data independent of any implementation.

Java provides many ADTs in the Collection and Map interfaces under the java.util package.

Examples of ADTs: 
	List, Queue, Deque, Stack


---
##### Data Structures

A data structure is an implementation of an ADT.

An ADT is an interface. A data structure is a class that implements that interface.  
Data structures are the concrete classes that implement the Collection and Map interfaces.  

Examples of data structures: 
	ArrayList, LinkedList, HashSet, TreeSet, HashMap, TreeMap



---
##### ADTs And Data Structures

**List :** 
	An ADT that consists of an ordered, indexed collection of values, where the same value may be stored more than once.

**List Methods :** 
	• add(index, object) – adds an object at a given index  
	• remove(index) – removes the object at the given index  
	• set(index, object) – sets value at index to be object  
	• get(index) – gets the object at index  
	• size() – returns the number of elements in the list  
	• isEmpty() – returns true if the list is empty, false otherwise
	• clear() – removes everything from list  
	• add(object) – adds object to end of list  
	• remove(object) – removes object from the list  
	• indexOf(object) – returns first index of object in list  
	• contains(object) – returns true if object in list, false otherwise


**Linked Lists :** 
	Linked List is a linear (recursive) data structure – a sequence of nodes.  
	Each node contains data (one or more elements/objects) and a reference to the next node in the sequence.

The nodes form a chain representation of the list as follows.
![[Screenshot 2025-02-10 at 8.32.11 AM.png]]
