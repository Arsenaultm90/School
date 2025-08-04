#### Red-Black Tree
A **Red-Black Tree (RBT)** is a binary search tree that **automatically stays balanced** as you insert and delete nodes, ensuring efficient operations.

Keeps the height of the tree approximately **log(n)**
Guarantees **O(log n)** time for:
- Insertion
- Deletion
- Lookup


**Bounded height :**
If a Red-Black Tree has `n` nodes, its height `h` satisfies:
$$h≤2log⁡2(n+1)$$
So it's at most **twice the height of a perfectly balanced binary tree**
This bounded height ensures:
- **O(log n)** time for search, insert, and delete
- The tree **does not degenerate** into a linear list (like a regular unbalanced BST could)


**Properties :**
- **Each node is either red or black.**
- **The root is always black.**
- **All leaves (null/NIL nodes) are black.**
- **If a node is red, then both its children are black.**  
    → _(No two reds in a row!)_
- **Every path from a node to its descendant leaves has the same number of black nodes.**  
    → _(Called the **black-height**)_

|Operation|Max Rotations|Max Recolorings|Time Complexity|
|---|---|---|---|
|Insert|≤ 2|≤ log(n)|O(log n)|
|Delete|≤ 3|≤ log(n)|O(log n)

|Operation|Time|
|---|---|
|Search|O(log n)|
|Insert|O(log n)|
|Delete|O(log n)|


---
#### Binary Trie

A **binary trie** is a tree where:
- Each **bit of an integer** is a level in the tree
- At each node:
    - **left (0-bit)** child → for 0 in that bit position
    - **right (1-bit)** child → for 1 in that bit position

This creates a **path per element** through the bits of its binary representation.

To find a specific number, follow its binary representation bit by bit.
If you hit a dead end (the path doesn't exist), backtrack and take the next "higher" option

##### The Backtracking Strategy
When you can't follow the exact path for your target number:
1. **Go back up** to the last decision point where you could have gone "higher"
2. **Take the higher branch** (go right/1 instead of left/0)
3. **Then go as far left as possible** from there to get the smallest number with that new prefix



---
#### 2-3-4 Tree

A **2–4 tree** (also called a 2-3-4 tree) is a **self-balancing multiway search tree** where:
- Each **node can have 1, 2, or 3 keys**, and **2, 3, or 4 children**
- All **leaves are at the same depth**
- The tree **automatically balances itself during insertion and deletion**

When a node has 3 keys (4-node), and you try to insert another, it’s **overfull**. You:
- **Split** it into two smaller nodes with 1 key each
- **Promote** the middle key up into the parent

If the **parent is also a 4-node**, it **recursively splits upward**

![[Pasted image 20250623075225.png]]



