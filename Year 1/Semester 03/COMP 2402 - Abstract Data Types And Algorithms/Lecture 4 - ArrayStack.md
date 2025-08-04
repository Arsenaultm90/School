![[ArrayStack 1.png|500]]

| "ArrayStack" name    | An array-based data structure that can behave like a stack _and_ support other list ops (legacy naming) |
| -------------------- | ------------------------------------------------------------------------------------------------------- |
| Dynamic array<br>    | An array that resizes itself automatically to grow or shrink<br>                                        |
| Resizing             | Copying elements into a bigger array when capacity runs out                                             |
| Amortized complexity | Although resizing is costly, the average cost per operation stays low over time                         |

**Memory Accesses (Big O Notation)**
size() : O(1)
push() : O(1)
pop() : O(1)


---
#### List Interfaces

get(i)
	1 bounds check, 1 memory access
	O(1)

set(i, x)
	1 bounds check, 1 memory access
	O(1)

add(i, x)
	2(n-i) + 1  Amortized Analysis
	O(n - i)

remove(i)
	2(n - i) - 1 Amortized Analysis
	O(n - i)

resize()
	We resize when 3n $\le$ a.length()


For every m add operations, we copy 2m elements.  
For every m remove operations, we copy 2m elements.  
Therefore the time spent in resize() is O(m), where m is the number of add and remove operations performed.
