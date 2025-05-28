A SEList (space-eﬃcient list) reduces this wasted space using a simple idea: Rather than store individual elements in a DLList, we store a block (array) containing several items. More precisely, an SEList is parameterized by a block size b. Each individual node in an SEList stores a
block that can hold up to b + 1 elements.

A SEList is then a doubly-linked list of blocks:

```
class Node {
	BDeque d;
	Node prev, next;
}
```


Unless a block is the last block, then that block contains at least b−1 and at most b + 1 elements. 
This means that, if an SEList contains n elements, then it has at most `n/(b−1) + 1 = O(n/b)` blocks.


---
#### Finding Elements

**Get Location**
```
Location getLocation (int i):  
	if (i < n/2):  
		Node u = dummy .next;  
		
		while (i >= u.d.size ()):  
			i -= u.d.size ();  
			u = u.next;  
		return new Location (u,i);  
	else:  
		Node u = dummy ;  
		int idx = n;  
		
		while (i < idx ):  
			u = u.prev;  
			idx -= u.d.size ();  
	return new Location (u, i - idx );
```

**Get and Set**
```
E get(i):  
	// check bounds  
	Location loc = getLocation (i);  
	return loc.u.d.get(loc.j);  

E set(i,x):  
	// check bounds  
	Location loc = getLocation (i);  
	return loc.u.d.set(loc.j, x);
```

Both runtimes are dominated by getLocation(): `O(min{i, n − i}/b)`


---
#### Adding Elements

**Add**
```
add(i, x):  
	if (i == n):  
		add(x); return ;  
		
	Location loc = getLocation (i);  
	Node u = loc.u;  
	r = 0; // keep count of the blocks  
	
	while (r < b && u != dummy && u.d.size ()==b+1):  
		u = u.next;  
		r++;  
		
	if (r == b): //b blocks are full  
		spread (loc.u);  
		u = loc.u; // reset u since no shifting required
		
	if (u == dummy ): // ran off the end , add new block  
		u = addBefore (u);  
		
	while (u != loc.u): // working backwards shifting elements  
		// move an element from u.prev to u  
		u.d. addFront (u.prev.d. removeBack ());  
		u = u.prev;  
		
	u.d.add(loc.j, x);  
	n++:
```

Time Complexity :
`O(b + min{i, n − i}/b)`


---
#### Spread and Gather

**Spread**
```
spread (Node u):  
	Node w = u;  
	
	// find the b-th node from u  
	for (i = 0; i < b; ++i):  
		w = w.next;  
	w = addBefore (w); // w is now the empty Node  
	
	while (w != u):  
		while (w.d.size () < b):  
			w.d. addFirst (w.prev.d. removeLast ());  
	w = w.prev
```

**Gather**
```
gather (Node u):  
	Node w = u;  
	
	for (i = 0; i < b -1; ++i):  
		while (w.d.size () < b):  
			w.d. addlast (w.next.d. removeFirst ());  
		w = w.next;  
	remove (w)
```


Time Complexity : O($n^2$)


---
#### Summary

Ignoring calls to spread() and gather(), SELList supports the operations:  
	get(i), set(i,x), size()  : `O(1+min{i, n-i}/b)`
	add(i,x) and remove(i)  : `O(b+min{i, n-i}/b`

Furthermore, starting with an empty SELList and performing a sequence of m add(i,x) and remove(i) operations results in `O(bm)` time spent in calls to spread() and gather().