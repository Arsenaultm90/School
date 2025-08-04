A **hash table** is a data structure that allows you to store **key-value pairs** and retrieve values based on their keys in **average-case O(1)** time.

You can think of it as a dictionary:
- Keys: unique identifiers (e.g., strings like `"username"`)
- Values: data associated with those keys (e.g., a user’s email)

Example :

```
HashMap<String, Integer> ageMap = new HashMap<>();
ageMap.put("Alice", 25);
ageMap.put("Bob", 30);
```


---
#### How it works internally:

**Step 1: Hash Function**
Every key is passed through a **hash function** to convert it to an integer (called a **hash code**).

```
int hashCode = key.hashCode();  // Java
```


**Step 2: Index Calculation**
The hash code is then mapped to a valid **array index** using modulus:

```
int index = hashCode % array.length;
```


**Step 3: Storage**
The array (often called a **bucket array**) stores the data at the computed index. There are two common ways of handling collisions:
1. **Separate Chaining**
	Each array slot holds a **linked list** (or another data structure) of all entries that hash to the same index.
2. **Open Addressing**
	Instead of using a list, it looks for the **next open slot** in the array (e.g., linear probing or quadratic probing).


---
#### Summary :

| Concept       | Explanation                                                            |
| ------------- | ---------------------------------------------------------------------- |
| Hash Table    | A key-value store with fast average-case lookup, insert, delete (O(1)) |
| Hash Function | Converts key to integer (hash code)                                    |
| Indexing      | `index = hash(key) % capacity` maps hash to array slot                 |
| Collisions    | Two keys hash to the same index → use chaining or probing              |
| Resizing      | Table resizes (rehashes) when load factor is too high                  |
| Use Case      | Dictionaries, caches, symbol tables, key lookups                       |
| Java Class    | `HashMap<K, V>`                                                        |


---
#### Collisions

For the sake of this course we are limiting our collision solutions to linear probing. 

Perform the hash function to find the index where the data will be stored. If a collision exists(index already has data), then start at `index + 1` and move through the array looking for a NULL index. 

If `#NULL < array.length/2`, then we resize the array by increasing the dimension in the form of $2^{dimension}$. We then rehash each element of the previous array to insert at their new indices and then hash the values to be added. 


##### Multiplicative Hashing
**Multiplicative hashing** is a method used in hash tables to compute a hash index from a key using multiplication.

The general formula for **multiplicative hashing** is:

$$h(k)=⌊m⋅((k⋅A)\; \% 1)⌋$$
$$h(x)=\frac{(z \times x)\; \%\; 2^w​}{2^{w-d}}$$

| Symbol | Meaning                                                                             |
| ------ | ----------------------------------------------------------------------------------- |
| x      | The key you want to hash                                                            |
| z      | An odd integer constant chosen randomly                                             |
| w      | The word size (number of bits in your machine word, e.g., 32 or 64)                 |
| d      | The number of bits you want in your hash output (the hash table size will be $2^d$) |

**Darryl's Multiplicative Hashing Method**
	Convert value to binary
	Assign bit values to array indices -> `[00][01][10][11]`
	Take the 'd' MSB in your binary number
	Insert at the index of that 2-bit binary value

Example :
w = 4
d = 2
z = 1
hash(7) = 7 x z = 7
7 = 0111
the array index is '01'



##### Chained Hash Table
A **chained hash table** is a type of hash table that handles **collisions** by **storing multiple items at each index** using **linked lists (or chains)**.

```
Index   Contents
  0     → [ ]
  1     → [12]
  2     → [42 → 22 → 2]
  3     → [7]
  4     → [ ]

```

| Collision handling | Use linked lists at each index      |
| ------------------ | ----------------------------------- |
| Insert time        | O(1) average (with good hash)       |
| Lookup time        | O(1) average, O(n) worst-case       |
| Deletes            | Simple if using doubly linked lists |









