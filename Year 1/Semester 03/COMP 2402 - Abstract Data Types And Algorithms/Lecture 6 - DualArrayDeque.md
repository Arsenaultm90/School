A DualArrayDeque represents a list using two ArrayStacks. Recall that an ArrayStack is fast when the operations on it modify elements near the end. A DualArrayDeque places two ArrayStacks, called front and back, back-to-back so that operations are fast at either end.

```
List<T> front;
List<T> back;
```

A DualArrayDeque does not explicitly store the number, n, of elements it contains. 
It contains `n = front.size() + back.size();` elements.

The front ArrayStack stores the list elements that whose indices are 0,..., front.size()−1, but stores them in reverse order. 

The back ArrayStack contains list elements with indices in front.size(),...,size()−1 in the normal order.


---
#### Get and Set
```
T get(int i) {
	if (i < front.size()) {
		return front.get(front.size()-i-1);
	} else {
		return back.get(i-front.size());
	}
}

T set(int i, T x) {
	if (i < front.size()) {
		return front.set(front.size()-i-1, x);
	} else {
		return back.set(i-front.size(), x);
	}
}
```


---
#### Add

```
void add(int i, T x) {
	if (i < front.size()) {
		front.add(front.size()-i, x);
	} else {
		back.add(i-front.size(), x);
	}
	balance();
}
```

**Runtime of Add**
O(1 + i)     if i <n/4
O(n)          if n/4 ≤i <3n/4
O(1 + n−i) if i ≥3n/4

The running time of add(i,x), if we ignore the cost of the call to balance(), is O(1 + min{i,n−i})

---
#### Remove

```
T remove(int i) {
	T x;
	
	if (i < front.size()) {
		x = front.remove(front.size()-i-1);
	} else {
		x = back.remove(i-front.size());
	}
	balance();
	return x;
}
```

The remove(i) operation and its analysis resemble the add(i,x) operation and analysis.


---
#### Summary

A DualArrayDeque implements the List interface. Ignoring the cost of calls to resize() and balance(), a DualArrayDeque supports the operations :
	• get(i) and set(i,x) : `O(1)` 
	• add(i,x) and remove(i) : ` O(1 + min{i,n−i})`

