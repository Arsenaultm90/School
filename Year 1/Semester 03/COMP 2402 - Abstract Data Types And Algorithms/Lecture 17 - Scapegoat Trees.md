A **Scapegoat Tree** is a type of **binary search tree (BST)** that maintains balance **without storing balance factors or heights in nodes**, unlike AVL or Red-Black Trees.

Instead, it uses **partial rebuilding** of unbalanced subtrees when imbalance is detected.

- A Scapegoat Tree maintains a size invariant:  
    The **depth of any node** should not exceed  
    `log₃/₂(n) ≈ 1.709 * log₂(n)` where `n` is the number of inserted nodes (not necessarily current size due to deletes).
    
- **α (alpha)** is the balance threshold constant (commonly set to 0.75). It defines the maximum allowed weight imbalance for subtrees.
    
- When imbalance is detected (i.e., a node is too deep), the tree **rebuilds** the subtree rooted at the nearest "scapegoat" ancestor that violates the balance condition.
    
- Rebuilding is done by:
    1. Collecting all nodes in a subtree into a sorted array (in-order traversal).
    2. Building a new balanced subtree from the array.



---
##### **Finding The Scapegoat :**
When we insert a node and it ends up **too deep**, we know the tree is becoming **unbalanced**.

We fix this by walking back up the tree to find the **first ancestor node** where the **balance condition** is violated — that is, where one of its children has gotten **too big**.

This node is called the **scapegoat**, and we rebuild the subtree rooted at it.

- `q` is the **total number of nodes ever inserted** into the tree **without being deleted**.
- It's an **overestimate** of the current size of the tree (`n`) because we may have deleted nodes but not yet rebalanced the tree.

Using $\frac{\text{node.children}}{nodes}$, we can find where our scapegoat node is. We are looking for a ratio > $\frac{2}{3}$.

---
##### **Rebuild Tree :**
In a Scapegoat Tree, **rebuilds are triggered during insertion** when:
- The **depth** of the inserted node exceeds the allowed max depth:`depth > log₍₃⁄₂₎(q)
`
- Compute `log₍₃⁄₂₎(q)` = maximum allowed depth
- Track the depth of each inserted node
- Compare it to the limit
- If the limit is exceeded, a rebuild is triggered

