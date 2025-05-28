Rounded to nearest 100
1. 
	a) 800
	b) 300
	c) 0
	d) 400
	e) 300
	f) 0
	g) 100
	h) 100

2.  ArrayDeque Methods
**remove() :**
```
public T remove(int i) {  
    if (i < 0 || i > n - 1)    throw new IndexOutOfBoundsException();  
    T x = a[(j+i)%a.length];  
    if (i < n/2) {  // shift a[0],..,[i-1] right one position  
       for (int k = i; k > 0; k--)  
          a[(j+k)%a.length] = a[(j+k-1)%a.length];  
       j = (j + 1) % a.length;  
    } else { // shift a[i+1],..,a[n-1] left one position  
       for (int k = i; k < n-1; k++)  
          a[(j+k)%a.length] = a[(j+k+1)%a.length];  
    }  
    n--;  
    if (3*n < a.length) resize();  
    return x;  
}
```

**removeFirst() :**
```
if n <= 0 return null;  
E temp = a[j];  
a[j] = null;  
n--;  // Decrease number of elements
j++;  // Increase first index position
return temp;
```

**removeLast() :**
```
if n <= 0 return null;  
E temp = a[j+n -1];  // Store remove element
a[j+n -1] = null; // Set index to null 
n--;  // Decrease number of elements
return temp;
```

**addFirst(x) :**
```
j = (j - 1 + a.length) % a.length; // Find index
a[j] = x; // Assign value
j--;  // Decrement first index
n++; // Increment total elements
if (3*n < a.length) resize();  // Check for resize
```

**addLast(x) :**
``` 
a[j+n] = x;  
n++;
if (3*n < a.length) resize();  
```


3. Rootish Array Stack
$$\displaylines{\frac{(b+1)(b+2)}{2} \ge i + 1 \\ \\
\frac{b(b+1)}{2} = \text{Sum of values } \\ \\ \\ \\
\text{Brute Force OR Quadratic Equation} \\
\frac{-b \pm \sqrt{ b^2 - 4ac }}{2a} \\ \\ 
b^2 + 3b - 2i \\ = 38 (\text{rounded up}) \\ \\
\frac{(38 + 1)(38 + 2)}{2} \ge 746 + 1 \\
\frac{39*40}{2} \ge 747 \\
780 \ge 747 \\
\text{This tells us the BLOCK INDEX.} \\ \\
\frac{38(38+1)}{2} \\
\frac{38(39)}{2} \\
= 741 (\text{Sum of all blocks before}) \\ 
746 - 741 = 5 \\ \\
∴ \text{Location of index 746 is } (38, 5).}$$


4. SkipList
Create skiplist

Find position on skiplist
	Start at top at sentinel node
	Check right 
	Move down or right
	repeat checks

Insert node on skiplist
	Use prev array to reassign node pointers
	Continue up the list of prev, inserting the node at each index until height is reached

