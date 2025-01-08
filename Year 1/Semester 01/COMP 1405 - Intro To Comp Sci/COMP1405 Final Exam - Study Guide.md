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
##### Data Structures/Variables
int - `my_number : int = 0` 
float - `my_decimal : float = 0.0`
string - `my_string : str = "Hello, World!"`
list - `my_list : list = []`
tuples - `my_tuple : tuple = (1, 2)`
dictionary - `my_dictionary : dictionary = {1: "One"}`
set - `my_set : set = {1, 2, 3, 4, 5, 4, 3, 2, 1}`


##### Dictionary Methods

| Name         | Description                                                                                                 |
| ------------ | ----------------------------------------------------------------------------------------------------------- |
| clear()      | Removes all the elements from the dictionary                                                                |
| copy()       | Returns a copy of the dictionary                                                                            |
| fromkeys()   | Returns a dictionary with the specified keys and value                                                      |
| get()        | Returns the value of the specified key                                                                      |
| items()      | Returns a list containing a tuple for each key value pair                                                   |
| keys()       | Returns a list containing the dictionary's keys                                                             |
| pop()        | Removes the element with the specified key                                                                  |
| popitem()    | Removes the last inserted key-value pair                                                                    |
| setdefault() | Returns the value of the specified key. If the key does not exist: insert the key, with the specified value |
| update()     | Updates the dictionary with the specified key-value pairs                                                   |
| values()     | Returns a list of all the values in the dictionary                                                          |


---
##### Condition Operators

```
= #Assignment
== #Comparison
< #Less Than
> #Greater Than
(>=, <=) #Less/Greater Than or Equal To
```


---
##### Functions
```
def main():
	pass

def my_function(default: str = "variables")

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
##### Slicing
```
my_list = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Basic slicing: Get elements from index 2 to 5 (exclusive) print(my_list[2:5]) 
# Output: [2, 3, 4] 

# Slice with step: Get every 2nd element from index 1 to 8 print(my_list[1:8:2]) 
# Output: [1, 3, 5, 7] 

# Slice from the beginning up to index 4 (exclusive) print(my_list[:4]) 
# Output: [0, 1, 2, 3] 

# Slice from index 6 to the end print(my_list[6:]) 
# Output: [6, 7, 8, 9] 

# Slice the entire list with a step of 2 print(my_list[::2]) 
# Output: [0, 2, 4, 6, 8] 

# Reverse the list print(my_list[::-1]) 
# Output: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
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

Base Case: The condition that stops the recursion.

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
