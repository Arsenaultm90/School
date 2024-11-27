<center><h2>Summation</h2></center>
<h3>Constants:</h3>
$$ \sum_{i=0}^{n}x = x(n-i+1)  $$

<h3>Variables:</h3>
$$ \sum_{i=0}^{n}i = n(\frac{n+1}{2}) $$


---

<center><h2>Selection Sort</h2></center>

```
def selectionSort(array, size):
    for ind in range(size):
        min_index = ind
        for j in range(ind + 1, size):
            # select the minimum element in every iteration
            if array[j] < array[min_index]:
                min_index = j

         # swapping the elements to sort the array
        (array[ind], array[min_index]) = (array[min_index], array[ind])
```

<h4>Analysis</h4>
	Number of Accesses: 4 in outer loop swap, 2 in inner loop
	Number of iterations: (n-1) in outer loop, (n-2) in inner loop

<center></center>
<h4>
	Sigma Notation</h4>
$$\sum_{i=0}^{n-2} 4 + 2(n-1-i)$$
$$\sum_{i=0}^{n-2} 4 + \sum_{i=0}^{n-2} 2(n-1) - \sum_{i=0}^{n-2} 2i $$
$$ \sum_{i=0}^{n-2} 4 + 2\sum_{i=0}^{n-2} (n-1) -2\sum_{i=0}^{n-2} i $$
$$ 4(n - 1) + 2(n-1)(n-1) - 2(\frac{(n-2)(n-1)}{2}) $$
$$ n^2 + 3n - 4 $$


---


<center><h2>Bubble Sort</h2></center>

```
def bubble_sort(arr):
  
    # Outer loop to iterate through the list n times
    for n in range(len(arr) - 1, 0, -1):
        
        # Initialize swapped to track if any swaps occur
        swapped = False  

        # Inner loop to compare adjacent elements
        for i in range(n):
            if arr[i] > arr[i + 1]:
              
                # Swap elements if they are in the wrong order
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                
                # Mark that a swap has occurred
                swapped = True
        
        # If no swaps occurred, the list is already sorted
        if not swapped:
            break
```

#### Analysis

Number of Accesses: 4
Number of Iterations: n

#### Sigma Notation
$$ \sum_{i=1}^{n}4(n-i) $$
$$ 4\sum_{i=1}^{n}(n-i) $$
$$ 4(\sum_{i=1}^{n}n - \sum_{i=1}^{n}i) $$
$$ 4(\sum_{i=1}^{n}n(n-i+1) - \sum_{i=1}^{n}n(\frac{n+1}{2})) $$
$$ 4(\sum_{i=1}^{n}n^2 - \sum_{i=1}^{n}n(\frac{n+1}{2}) $$
$$ 2n^2 -2n $$



---
