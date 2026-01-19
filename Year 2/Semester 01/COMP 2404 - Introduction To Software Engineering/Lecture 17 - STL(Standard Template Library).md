The STL is a collection of **generic, reusable components** that work with any data type.  
It is built on **three core pillars**:
1. **Iterators**
2. **Containers**
3. **Algorithms**

Everything in the STL is designed so these three parts work together seamlessly.


---
#### **ITERATORS**

##### What is an Iterator?
An iterator is like a **pointer-like object** that allows you to:
- Traverse through container elements
- Access element values
- Insert or erase elements (for some containers)

Almost all STL algorithms operate **only through iterators**, NOT directly on containers.  
Example: `sort(vec.begin(), vec.end())`

##### Types of Iterators
The STL defines **five** iterator “capabilities,” each with different powers.

**1. Input Iterator**
- Can read from the container
- Moves forward only
- Example: reading from `std::istream_iterator`

**2. Output Iterator**
- Can write to a container
- Moves forward only
- Example: `std::back_inserter(vec)`

**3. Forward Iterator**
- Read & write
- Moves forward
- Example: `std::forward_list<T>::iterator`

**4. Bidirectional Iterator**
- Read & write
- Moves forward and backward
- Example: `std::list<T>::iterator`, `std::set<T>::iterator`

**5. Random Access Iterator**
- Read & write
- Moves forward/backward
- Jumps to any element in constant time (`it += 5`, `it[3]`)
- Example: `std::vector<T>::iterator`, `std::deque<T>::iterator`

For `vector` → it _is_ a pointer  
For `list` → it contains a pointer to a node  
For `map` → it contains a pointer + navigation info  
For `deque` → it contains block index + element index

**Common Iterator Functions**
Every container supports these:

|Operation|Meaning|
|---|---|
|`begin()`|Iterator to first element|
|`end()`|One past last element|
|`rbegin()`|Reverse iterator to last|
|`rend()`|One before first|


```
 vector   .<Student> ::iterator&  stuIt
\______/   \______/   \________/  \___/
  |           |          |         |
  |           |          |         └── variable name
  |           |          |
  |           |          └──────────── reference (output parameter)
  |           |
  |           └──────────────────────── iterator type for a Student vector
  |
  └──────────────────────────────────── templated vector container

```



Example:
```
vector<int> v = {1, 2, 3, 4};

for (auto it = v.begin(); it != v.end(); ++it) {
    cout << *it << " ";
}
```




---
##### **CONTAINERS**

A container is a data structure that **stores objects**.  
STL containers fall into 4 categories:
1. **Sequence Containers**
	Store elements **in a linear order**.
	 **1. `vector`**
	- Dynamic array
	- Fast random access (O(1))
	- Fast push_back (amortized O(1))
	- Slow insert/erase in the middle (O(n))
	
	**2. `deque`** (double-ended queue)
	- Fast push_front and push_back
	- Random access supported
	- Internally multiple blocks
	
	**3. `list`**
	- Doubly linked list
	- Fast insert/erase anywhere (O(1))
	- No random access
	
	**4. `forward_list`**
	- Singly linked list    
	- Memory-efficient but only forward iteration
	
	**5. `array`**
	- Fixed-size array wrapper (C-like but safer)

2. **Associative Containers**
	Tree-based (red-black tree).  
	Store elements **in sorted order**.
	**1. `set`**
	- Stores **unique** keys
	- Sorted
	- O(log n) search/insert
	
	**2. `multiset`**
	- Like set but allows **duplicates**
	
	**3. `map`**
	- Key/value pairs
	- Unique keys
	- Sorted
	- Example: dictionary
	
	**4. `multimap`**
	- `map` but allows duplicate keys

3. **Unordered (Hash) Containers**
	Use **hash tables**, so order is NOT sorted.
	Includes:
	- `unordered_set`
	- `unordered_multiset`
	- `unordered_map`
	- `unordered_multimap`
	
	Properties:
	- Average O(1) search/insert/erase
	- Worst-case O(n)
	- Very fast for lookup heavy tasks

4. **Container Adapters**
	Provide a **restricted interface** on top of other containers.
	**1. `stack`**
	- Uses deque by default
	- LIFO
	- `push()`, `pop()`, `top()`
	
	**2. `queue`**
	- FIFO
	- `push()`, `pop()`, `front()`
	
	**3. `priority_queue`**
	- Max-heap by default
	- Grab largest element efficiently
	- O(log n) insert


---
#### **ALGORITHMS**

Algorithms are **prebuilt functions** that work on iterators, not containers.  
They do things like searching, sorting, counting, transforming…

Located in: `<algorithm>` and `<numeric>`.

---
#### **Major Categories of Algorithms**

**A. Searching & Counting**
```
find(begin, end, value)
count(begin, end, value)
binary_search(begin, end, value)   // requires sorted data
```

**B. Sorting**
```
sort(begin, end)         // QuickSort/IntroSort (very fast)
stable_sort(begin, end)  // preserves order of equal values
partial_sort(begin, middle, end)
```

**C. Modifying Algorithms**
```
reverse(begin, end)
rotate(begin, mid, end)
fill(begin, end, value)
replace(begin, end, old, new)
remove(begin, end, value)
```

**D. Non-modifying Algorithms**
```
for_each(begin, end, func)
all_of, any_of, none_of
find_if(begin, end, pred)
max_element, min_element
```

**E. Numeric Algorithms** (in `<numeric>`)
```
accumulate(begin, end, initial_value)
inner_product(...)
iota(begin, end, start_value)   // fill with sequence
```

**F. Copying Algorithms**
```
copy(begin, end, dest)
copy_if(begin, end, dest, pred)
move(begin, end, dest)
swap_ranges()
```

**G. Set Algorithms** (for sorted ranges)
```
set_union()
set_intersection()
set_difference()
set_symmetric_difference()
```

**H. Heap Algorithms**
Used under the hood by `priority_queue`.
```
make_heap(begin, end)
push_heap(begin, end)
pop_heap(begin, end)
```


---
#### **How All Three Parts Work Together**

Example: sort a vector
```
vector<int> v = {5, 3, 9, 1};

sort(v.begin(), v.end());
```
- **Container:** `vector`
- **Iterator:** `v.begin()` / `v.end()` are random-access iterators
- **Algorithm:** `sort()` works because random access iterators are supported



---
Lambdas (Anonymous Functions)


```
[]() {

}

[] - Captures external variables
() - Parameters for function
{} - Function definition
```


