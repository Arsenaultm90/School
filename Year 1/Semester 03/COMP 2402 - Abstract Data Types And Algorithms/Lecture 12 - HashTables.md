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







