A heap is a specific type of binary tree with two defining properties:
	**Shape Property:**
		- It is a complete binary tree
		- Every level is full except possibly the last
		- The last level is filled left to right
	**Heap-Order Property:**
		- Min-heap:  
		    Every parent ≤ its children  
		    Smallest element is at the root
		- Max-heap:  
		    Every parent ≥ its children  
		    Largest element is at the root


A heap is **not sorted**. Only parent–child relationships are guaranteed.
Offer dynamic min/max access.

#### Runtime
Find min/max : O(1)
Insert : O(log n)
Removal: O(log n)
Total Runtime : O(n log n)

The range of indices a value can have is $2^d - 2^{d+1} - 1$. Where $d$ is the number of ancestors before the value. A node can only be the $k_{th}$ smallest if it has at most $k−1$ ancestors.

Example : 
	What indices can a value of 4 exist within a heap of increment values up to 2026?
	If a node is at depth ≥ 4, it has at least 4 ancestors.
	That means it must be ≥ 4 distinct values above it.
	So it **cannot** be the 4th smallest.
	The 4th smallest value must lie at **depth ≤ 3**, meaning:
		$\boxed{\text{indices } 2 \text{ through } 15}$

At depth d, the indices are:

$2^d \le i \le 2^{d+1}-1$

For the 4th smallest, $d \le 3$
So the max index occurs at $d=3$:
	$2^{3+1}-1 = 2^4 - 1 = 16 - 1 = 15$

And the minimum index (besides the root) is 2.



---
# Array Representation

Because the tree is complete, we store it in an array:
	For index `i` (1-based indexing):
		- **Parent**: `i/2`
		- **Left child**: `2i`
		- **Right child**: `2i + 1`
		- **Height:** `log n`



---
# Heap Functions

**Max/Min Value :** O(1)
```
// Return largest value
max(A):
	return A(1);
```


**Insert Value :** O(log n)
```
// Replace value at index
increase_key(A, i, x):
	set A(i) = x;
	
	while(i > 1 && A(parent(i)) < A(i)):
		swap A(i) <-> A(parent(i));
		i = parent(i);
```


**Insert Value :** O(log n)
This operation assumes that $A[1....n]$ is heap and $1 \leq n < N$; thus there is new space for element $x$.
```
// Insert value at end of heap
insert(A, x):
	n = n+1;
	A[n] = -infinity
	increase_key(A, n, x)
```


**Heapify :** O(log n)
This operation assumes:
	$1 \leq i \leq n$
	subtree rooted at left(i) is a heap
	subtree rooted at right(i) is a heap
	At termination: subtree rooted at i is a heap
```
heapify(A, i):
	l = left(i)
	r = right(i)
	
	if l <= n && A[l] > A[i]:
		then max = l
	else max = i
	
	if r <= n && A[r] > A[max]:
		then max = r
	
	if max != i:
		then swap A[i] and A[max];
		heapify(A, max)

```

Time = O(1) + time for a recursive call at a node one level lower in the tree.
	= O(height) = (log n)


**Build Heap :** O(N)
input: array $A[1\dots N]$
output: heap $A[1\dots N]$

$n = N$
for $i =$ $\frac{n}{2}$ down to 1 : heapify(A, i); // First non-leaf index
$A = [4, 1, 3, 2, 16, 9, 10, 14, 8, 7]$, N = 10

$i$ starts at $n/2 = 5$, because $A[6]$ to $A[10]$ are just leaves and the subtree rooted at a leaf is a heap.

In General : All $A[i]$, $\frac{n}{2} + 1 \leq i \leq N$, are leaves.

Running Time :
	$1 · h + 2(h-1) + 2^2(h-2) + \dots + 2^{h-1} · 1$
	$\sum^h_{i=1} 2^{h-i} · i$
	 $2^h \sum^h_{i=1} \left( \frac{1}{2} \right)^i · i$
		 $2^h = N$
	O(N)


Heap Sort : O(N log N)


---
# K-Way Merge

A **k-way merge** means:
	Given **k sorted lists**, merge them into one single sorted list.

1. Put the **first element of each list** into a **min-heap of size k**
2. Repeat:
    - Extract the minimum (this is the next sorted output)
    - Insert the next element from the same list into the heap

Heap size never exceeds k.

Each operation: $O(\log k)$
Total time: $O(n \log k)$


