##### Python Syntax

```
my_variable : int = 0 #Declare a variables

def my_function(): #Declare a function
	return 0

for i in range(0, 10, 1): #For loop (Start, Stop, Step)
	print(i)

while True: #While loop
	print(True)
```


---
##### Data Structures
int - `my_number : int = 0` 
float - `my_decimal : float = 0.0`
string - `my_string : str = "Hello, World!"`
list - `my_list : list = []`
tuples - `my_tuple : tuple = (1, 2)`
dictionary - `my_dictionary : dictionary = {1: "One"}`
set - `my_set : set = {1, 2, 3, 4, 5, 4, 3, 2, 1}`

---
##### Functions
```
def main():
	pass

#Sets main to program start
if __name__ == "__main__":
	main()
```


---

##### Loops

**Pre-Condition**
```
i : int = 0

while i < 5:
	i += 1
```

**Post-Condition**
```
while True:
	if x == 1:
		break
```


---

##### File I/O

```
file_name : str = "text.txt"

# File stream will close after the code below executes
with open(file_name, "r") as text_file:
	for i, line in enumerate(text_file, start=0):
		print(line.strip())
```

To create a new file in Python, use the `open()` method, with one of the following parameters:
	`"x"` - Create - will create a file, returns an error if the file exists
	`"a"` - Append - will create a file if the specified file does not exists
	`"w"` - Write - will create a file if the specified file does not exists
	`file.write()` - will add text to the file

---

##### Recursion

```
def time_warp(num_of_timewarps : int):
	if num_of_timewarps == 0:
		return "Let's do the time warp again"
		
	print(time_warp(num_of_timewarps - 1))
	
	return "Let's do the time warp again"
```

---

##### Searching and Sorting

**Bubble Sort** - $O(n^2)$
- **Description**: Repeatedly swaps adjacent elements if they are in the wrong order.
- **Key Feature**: Simple but inefficient for large datasets.
- **Best Case**: $O(n)$ (when the array is already sorted).
- **Worst/Average Case**: $O(n^2)$.

**Selection Sort** - $O(n^2)$
- **Description**: Divides the array into sorted and unsorted sections; repeatedly selects the smallest element from the unsorted section and swaps it with the first unsorted element.
- **Key Feature**: Easy to implement, but performance doesn't improve for partially sorted arrays.
- **Best/Worst/Average Case**: $O(n^2)$.

**Insertion Sort** - $O(n^2)$
- **Description**: Builds a sorted section one element at a time by inserting elements from the unsorted section into their correct position.
- **Key Feature**: Efficient for small or nearly sorted datasets.
- **Best Case**: $O(n)$ (when the array is already sorted).
- **Worst/Average Case**: $O(n^2)$.

**Merge Sort** - $O(n \log(n))$
- **Description**: Recursively splits the array into halves, sorts each half, and then merges the sorted halves.
- **Key Feature**: Stable and efficient for large datasets but uses additional memory.
- **Best/Worst/Average Case**: $O(n\log⁡n)$.

**Quick Sort** - $O(n \log(n))$
- **Description**: Divides the array using a pivot, partitions elements around the pivot, and recursively sorts the partitions.
- **Key Feature**: In-place sorting; performance depends on pivot choice.
- **Best/Average Case**: $O(n\log⁡n)$.
- **Worst Case**: $O(n^2)$(when pivot selection is poor, e.g., sorted array with the first or last element as pivot).
