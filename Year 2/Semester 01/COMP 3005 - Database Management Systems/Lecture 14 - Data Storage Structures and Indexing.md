#### **Indexing**

**Indexing** is a database technique used to **speed up data retrieval** operations on a table.  
Instead of scanning every row (called a **full table scan**), the DBMS uses an **index structure** to quickly locate the rows that match a query condition.

Think of an index like the index of a book:
- Without an index → you read the whole book to find a topic.
- With an index → you jump directly to the page number.


An **index** is typically created on one or more columns of a table (called **key fields**).
When you create an index:
```
CREATE INDEX idx_student_name ON Students(name);
```

The DBMS creates a separate **data structure** (often a **B-tree** or **B+ tree**) that stores:
- The indexed column values (keys)
- Pointers to the rows in the table

So when you run:
```
SELECT * FROM Students WHERE name = 'Alice';
```
the DBMS uses the index to find “Alice” quickly instead of scanning the entire table.


**Types of Indexes**
1. **Primary Index** – automatically created on the primary key; keys are unique and sorted.
2. **Secondary Index** – created manually on non-primary key columns.
3. **Clustered Index** – physically sorts data in the table according to the index key.
4. **Non-clustered Index** – maintains a separate index structure with pointers to the table rows.


---
#### **B-Trees**

A **B-tree (Balanced Tree)** is a self-balancing search tree used to store sorted data and allow searches, insertions, and deletions in **O(log n)** time.

It is optimized for systems that read and write **large blocks of data** (like disks).

A B-tree node contains:
- **Keys** (values from the indexed column)
- **Pointers** to child nodes
- **Pointers** to actual data records (for leaf nodes)

Each node can have multiple children (not just 2 like in a binary tree).

Example (simplified):
```
        [30]
       /    \
  [10,20]   [40,50]
```
- Keys are always **sorted**.
- Every node (except root) has between ⌈m/2⌉ and m children (for order m tree).
- The tree stays **balanced** — all leaves are at the same depth.

When searching for a value (say 45):
1. Start at the root.
2. Compare with keys to find which branch to follow.
3. Continue recursively until the key is found (or not found).
4. The leaf node points to the actual table record.

Because the tree is balanced, lookup time is **logarithmic** and consistent.


**B+ Tree**
A **B+ tree** is an **extension of the B-tree**, but it’s **more efficient for database indexing**.

Differences from a B-tree:
- **All actual data records (pointers to rows)** are stored **only in leaf nodes**.
- **Internal nodes** store only **keys** for navigation.
- **Leaf nodes** are **linked together** (like a linked list), which makes **range queries** fast.

Example:
```
          [30, 60]
         /    |     \
     [10,20] [40,50] [70,80,90]
        |        |         |
     (data)   (data)    (data)
```
- Internal nodes → guide the search
- Leaf nodes → contain the actual data references
- Leaf nodes are linked: `[10,20] → [40,50] → [70,80,90]`


**B+ Trees Are Preferred in Databases**
1. **Faster range queries**  
    Because leaf nodes are linked, finding all rows between two keys is sequential and fast.
2. **More keys per node**  
    Internal nodes only store keys, not data pointers, so trees are shorter and shallower.
3. **Better disk utilization**  
    Each node fits well into a disk block; fewer I/O operations are needed.
4. **Consistent performance**  
    All data is found at the leaf level (same number of I/Os for all lookups).


**Disk I/O Effiency**

|Concept|Explanation|
|---|---|
|**Each node fits in one disk block**|1 I/O per level|
|**Shallow tree (few levels)**|Only 2–4 blocks read per lookup|
|**Sequential leaf nodes**|Fast range scans with minimal random I/O|
|**Localized updates**|Only a few blocks modified per insert/delete|
|**Disk-friendly structure**|Designed for block-based I/O, not in-memory traversal|
