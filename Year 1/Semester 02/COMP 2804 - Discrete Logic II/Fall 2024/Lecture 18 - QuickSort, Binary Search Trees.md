#### Quick Sort

```
quicksort(a)
	if len(a) <= 1 : return a
	p = random.choice(a)
	return quicksort([x for x in a if x < p])
		+ [x for x in a if x == p]
		+ [x for x in a if x > p]
```


**Theorem :** 
	The expected number of comparisons done by quicksort when sorting an array of n distinct values is at most $2n\ln(n)$.





---
#### Binary Search Trees

**Theorem :** 
	If we search for $x + \frac{1}{2}$ for any $x \in \{0, \dots, n\}$ in a random binary search tree, then the expected length of the search path is $H_{x} + H_{n-x}$.

