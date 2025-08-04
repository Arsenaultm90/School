A **Binary Treap** is a combination of:
1. A **Binary Search Tree (BST)** — based on **keys**
2. A **Heap** — based on **priorities**

Each node contains:
- A **key** (used to maintain BST property)
- A **priority** (used to maintain heap property)


1. **BST Property**:
	- For any node `N`, all keys in the left subtree are **less than** `N.key`, and all in the right are **greater**.
 2. **Heap Property (Max-Heap or Min-Heap)**:
	- For a **max-heap treap** (common), `N.priority ≥ N.left.priority` and `N.priority ≥ N.right.priority`.

The idea is:
- Insert nodes like a BST by key
- Then rotate (like in AVL trees) to restore the heap property by priority



---
#### Meldable Heaps

A **meldable heap** is a type of binary heap that supports a special operation called **meld** (or **merge**) in addition to standard heap operations like `insert`, `findMin`, and `deleteMin`.

Unlike more rigid heaps like binary heaps or Fibonacci heaps, **meldable heaps use randomness** to allow flexibility in their structure.

This is simply the process of merging heaps together using recursive methods. 
	Choose the heap with the smaller root
	Randomly decide left or right branch
	Compare node with root of merging heap, choose lowest value
	Continue down the heap recursively comparing the nodes



