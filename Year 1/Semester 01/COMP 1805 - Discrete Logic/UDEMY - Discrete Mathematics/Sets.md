A '**Set**' is a collection of things(objects) that are referred to the elements of a set.

---
##### Number Sets

(ℕ) Natural Numbers : $\{1, 2, 3, 4, 5, \dots\}$ or $\{0, 1, 2, 3, 4, 5, \dots\}$
(ℤ) Integers : $\{..., -3, -2, -1, 0, 1, 2, 3, ...\}$
(ℚ)Rational Numbers : $\left\{ \frac{4}{2}, \frac{1}{2}, \frac{10}{4}, \dots \right\}$
(𝕀)  Irrational Numbers : $\{\pi, e, \sqrt{ 2 }, \dots\}$
(ℝ) Real Numbers : All Rational and Irrational numbers
(i)  Imaginary Numbers : $i = \sqrt{ -1 },\; i^2 = -1$
(ℂ)Complex Numbers : $a + bi$

![[Pasted image 20241129173212.png]]


---
##### Set Equality

 **The Axiom of Extensionality**
The axiom means that the two sets _A_ and _B_ are equal **if and only if** _A_ and _B_ have the same members. $$\displaylines{\forall x \forall y [\forall z (z \in x \leftrightarrow z \in y) \rightarrow x = y]}$$
Example:
$A = \{1, 3, 5, 1, 5, 5, 3\}$
$B = \{3, 1, 5\}$
	Both sets contain 1, 3, 5 and sets do not contain duplicates so they are considered equal.


---
##### Set-Build Notation

$A = \{-5, 4, 3, -10, -5, 2\}$
$\{x \in A | x > 0\}$ = $\{2, 3, 4\}$
$\{x \in A | x < 0\}$ = $\{-5, -10\}$

$\{x \in R| x^2 = 4\}$ = $\{-2, 2\}$

---
##### Types Of Sets

1. Universal Set - $U$, A set that contains all other sets.
2. Empty Set - $Null \; Set$, $∅$, $ɸ$, $\{\}$, A set that contain nothing.
3. Singleton Set - A set that is only one element
4. Finite Set - A set that contains a countable number of element.
5. Infinite Set - A set with an infinite number of elements.
6. Subset - A set that contains a subset of elements from a larger set.

**Cardinal Number Of A Set**
A count of the number of elements within a set.
A = {1,...,n}
n(A) = Cardinality

**Equivalent Sets**
A set is said to be equivalent if the cardinalities are the same.
**Notation:** $A \sim B$

**Equal Sets**
A set is said to be equal if the elements in the sets are the same.

---
##### Subsets
If $A$ and $B$ are sets, then $A$ is called a subset of $B$, if, and only if, every element of $A$ is also an element of $B$.
**Notation:** $A \subseteq B$

NOTE: The empty set is a subset of every set.

**Ex.**
$A = \{1, 2, 3, 4, 5\}$
$B = \{1, 2, 3, 4,\dots,100\}$

or

$A = \{1, 2, 3, 4, 5\}$
$B = \{1, 2, 3, 4, 5\}$

**Proper Subset**
There must be, at least, one element in $B$ that is not in $A$ for $A$ to be a proper subset. 
**Notation:** $A \subset B$

$A = \{1, 2, 3\}$
$B = \{1, 2, 3, 4\}$

---
##### Power Sets
A **Power Set** $A$ is the set of all subsets of $A$. 
For a given set, the cardinality of the **Power Set** will be $2^n$, where $n$ is the cardinality of a subset to the power set.
**Notation:** $P(A)$

Ex.
$B = \{a, b, c\}$
$A = \{\{  \}, \{ a \}, \{ b \}, \{ c \}, \{ a, b \}, \{ a, c \}, \{ b, c \}, \{ a, b, c \}\}$


---
##### Ordered Pairs
An ordering of objects such that, the ordering of the objects matters.

Ex.
$$\displaylines{A = \{ 1, 2, 3, 4 \}\\
B = \{ 2, 3, 1, 4 \}\\
∴A = B}$$
But if we have, $$\displaylines{(1, 2) \\(2, 1) \\ (1, 2) \neq(2, 1)}$$
The order matters. 


**Ordered $n$-Tuples**
$$\displaylines{(x_{1}, x_{2}, x_{3}, \dots, x_{n}) = (y_{1}, y_{2}, y_{3}, \dots, y_{n}) \\
(x_{1}, y_{1}) \;- Ordered\; Pair\; or\; Ordered\; 2-Tuples}$$

---
##### Cartesian Product
Given sets $A$ and $B$, the **Cartesian Product** of $A$ and $B$ is the set of all ordered pairs(a, b), where $a$ is in $A$ and $b$ is in $B$.
**Notation:** $A\;\times\;B$ = $\{(a, b)\; |\;a \in A\; and\; b \in B\}$

Ex.
$$\displaylines{A = \{1, 2\}\\
B = \{c, d\}\\
A \times B = \{(1, c), (1, d), (2, c), (2, d)\}}$$

---
##### Set Operations(Union & Intersection)
**Union($\cup$):** A set containing all the unique elements from set $A$ and set $B$.
**Intersection($\cap$):** A set containing all the unique elements that appear in both set $A$ and set $B$.
**Notation:** $$\displaylines{A \cup B = \{x\;|\;x \in A\; and\;x \in B\} \\
A \cap B = \{x\;|\;x \in A\; or\;x \in B\}}$$
Ex. $$\displaylines{Union\\A = \{1, 2, 3\}\\ B = \{4, 5, 6\}\\ A \cup B = \{1,2,3,4,5,6\}}$$
$$\displaylines{Intersction\\A = \{1, 2, 3, 4, 5, 6\} \\ B = \{2, 3, 4\} \\ A \cap B = \{2, 3, 4\}}$$

**Properties of Union & Intersection**
$$\displaylines{Commutative\; Law: A \cup B = B \cup A,\; A \cap B = B \cap A\\
Associative\;Law: (A \cup B) \cup C = A \cup (B \cup C),\; (A \cap B) \cap C = A \cap (B\cap C)\\
Distributive\;Law: A \cup (B\cap C) = (A \cup B) \cap (A \cup C),\; A \cap (B \cup C) = (A \cap B) \cup (A \cap C)\\
Empty\; Set: A \cup \{\;\} = A,\; A \cap \{\;\} = \{\;\}\\
Universal\; Set: A \cup U = U\\
Idempotent\; Law: A \cup A = A,\; A \cap A = A}$$

---
##### Set Operations(Difference & Complement)
**Difference(-):** A set containing all elements in set $A$ but not in set $B$.
**Complement($A^c$):** A set containing all elements not in set $A$.
**Notation:**$$\displaylines{A-B\\ A^c}$$

Ex. $$\displaylines{Difference\\A = \{1, 2, 3, 4\} \\
B = \{4, 5, 6\}\\
A - B = \{1, 2, 3\}\\ \\
Complement\\
U = \{1, 2,3, 4, 5, 6, 7\}\\
A = \{1, 2, 3\}\\
A^c = \{4, 5, 6, 7\}}$$
**Properties of Difference & Complement**
$$\displaylines{A \cup A^c = U\\
(A^c)^c = A\\
U^c = \{\;\}, \{\;\}^c = U\\
A-B = A \cap B^c}$$

---
##### Partition Of Sets
Disjoint Sets: Two set that have no elements in common. $A \cap B = \{\;\}$

A finite or infinite collection of non-empty sets $\{A_{1}, A_{2}, A_{3}, \dots\}$ is a partition of set $A$, is and only if: $$\displaylines{1.\; A\;is\;the\;union\;of\;all\;of\;the\;sets\\
2.\; The\;sets\;are\;mutually\;disjoint}$$
Ex.$$\displaylines{A = \{1, 2, 3, 4, 5, 6\}\\
A_{1} = \{1, 2, 3\}\\
A_{2} = \{3\}\\
A_{3} = \{4, 5, 6\}\\
∴\;\{A_{1}, A_{2}, A_{3}\}\;is\;a\;partition\;of\;A}$$
