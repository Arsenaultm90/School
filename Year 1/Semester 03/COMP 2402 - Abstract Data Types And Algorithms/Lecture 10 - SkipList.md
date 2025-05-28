A SkipList consists of linked lists horizontally. Vertically they are Nodes with an array of pointers.
Sorted order.

![[SkipList.excalidraw.png|300]]

get(), set(), add(), remove() : `O(log n)`


---
#### Find

1. Start from the top
2. Check next node and compare values. 
3. Move down if not found
4. If next node data is less than the node we want, move right. 
5. Repeat until the previous node is found. i.e. find(4) -> Node 3

![[Screenshot 2025-05-27 at 9.23.29 AM.png]]



---
#### Add

```
boolean add(x):  
	Node u = sentinel ;  
	r = h; c = 0;  

	// Loop until we reach the bottom of the linked list
	while (r >= 0): 
		// Loop until we find a valid node smaller than 'x' 
		while (u.next[r]!= null && c = compare (u.next[r].x,x) <0):  
			u = u.next[r];  
			if (u.next[r] != null && c = 0) return false ;  
		prev[r--] = u;

	// now use the prev to insert  
	Node w = new Node(x, pickHeight());  

	// Fill prev[] array with sentinel nodes on height > w.height
	while (h < w.height): prev[++h] = sentinel;  

	// Continue reassigning pointers until we reach the height
	for (i = 0; i < w.next.length; ++i):  
		w.next[i] = prev[i]. next[i];  
		prev[i]. next[i] = w;  
	n++;  
	return true;
```
