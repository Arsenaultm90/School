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

```
public class Node{  
	private Object data;  
	private Node next;  
	
	public Node(Object data, Node next){  
		this.data = data;  
		this.next = next  
	}  
//other methods  
}
```



**Queue :** 
	An ADT that stores elements in a first-in-first-out (FIFO) order. Elements are added at one end (head) and removed from the other (tail).

**Queue Methods :** 
	• add(object) – adds object to end of the queue  
	• remove() – removes/returns object at front of queue  
	• peek() – returns the object at front of queue  
	• isEmpty() – true if no items, false otherwise  
	• size() – returns the number of elements in the queue  
	• clear() – removes everything from queue



**Stack :** 
	An ADT that stores elements in a last-in-first-out (LIFO) order. Elements are added to and removed from the ‘top’ end only.

**Stack Methods :** 
	• push(object) – adds object to top of stack  
	• pop(object) – removes/returns item on top of stack  
	• peek() – returns item on top of stack  
	• isEmpty() – true if no items, false otherwise  
	• size() – returns the number of elements in the stack  
	• clear() – removes everything from stack


---
##### Summary

Abstract Data Type (Interface) vs. Data Structure (Class)  
ADT is a template.  
A Data Structure is an implementation of a given ADT.