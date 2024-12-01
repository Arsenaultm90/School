A **Relationship** is an association that expresses the way two or more entities are connected.
The **Cartesian Product** of $A$ and $B$ is the set of all possible ordered pairs of the form $(x, y)$ where $x \in A$ and $y \in B$.

**Binary Relation :**
	A **binary relation** R between two sets A and B is a subset of the Cartesian product $A×B$. That is:$$\displaylines{R⊆A×B}$$
	If $(a, b) \in R$, we say that $a$ is related to $b$ by $R$, often written as $a R b$.


---

 **Reflexive Relation :**
	A relation $R$ on $A$ is **reflexive** if every element in $A$ is related to itself.
	That is: $$\displaylines{\forall x \in A,\; (x, x) \in R}$$
	This means that for every $x$ in $A$, the pair $(x,x)$ must be included in $R$.
		Note: The 'is equal to' comparison is true for all pairs but does not define a reflexive relation in totality. It is a more restrictive variation of the relation.


---

**Symmetric Relation :**
	A relation on $R$ is **symmetric** if, when one element is related to another, the reverse is also true.
	That is: $$\displaylines{\forall a,b \in A (a\; R\; b \rightarrow b\;R\;a)}$$
	In other words, if the pair $(a,b)$ is in the relation $R$, then the pair $(b,a)$ must also be in $R$.


---

**Transitive Relation :**
	A relation on $R$ is **transitive** if, for all $a, b, c \in A$: $$\displaylines{\forall a, b, c \in A\; (a\; R\; b\; \land b\; R\; c) \rightarrow (a\; R\; c)}$$
	In other words, if $a$ is related to $b$, and $b$ is related to $c$, then $a$ must also be related to $c$.


---

**Equivalence Relation :**
	The relation $R$ is an **equivalence relation** if it satisfies the following three properties:
		1. **Reflexivity**: For all $a \in A, a R a$. Every element is related to itself.
		2. **Symmetry**: For all $(a,b) \in A$, if $a R b$, then $b\; R\; a$. If one element is related to another, the reverse is also true.
		3. **Transitivity**: For all $(a,b,c) \in A$, if $a R b$ and $b R c$, then $a R c$. If an element is related to a second, and the second is related to a third, then the first is related to the third.


---

**Partially Ordering Relation :**
	The relation $R$ is a **partial order** if it satisfies the following three properties:
	1. **Reflexivity**: For all $a \in A, a R a$. Every element is related to itself.
	2. **Antisymmetry**: For all $(a,b) \in A$, if $a R b$ and $b R a$, then $a=b$. If two elements are mutually related, they must be identical.
	3. **Transitivity**: For all $(a,b,c) \in A$, if $a R b$ and $b R c$, then $a R c$. If an element is related to a second, and the second is related to a third, then the first is related to the third.

---

**Properties Of Relations:**
Set Operations
	$A = \{1, 2, 3\},\;\ B = \{x, y, z\}$
	$R_{1} = \{(1, x), (2, x), (3, x)\},\;\ R_{2} = \{(1, x), (1, y), (1, z)\}$
	$R_{1} \cup R_{2} = \{(1,x), (1, y), (1, z), (2, x), (3, x)\}$
	$R_{1} \cap R_{2} = \{(1, x)\}$
	$R_{1} - R_{2} = \{(2, x), (3, x)\}$

Set Predicates
	$R_{1} = \{(a, b\; |\; a > b\}$
	$R_{2} = \{a, b\; |\; a = b - 1\}$
	$R_{1} \cup R_{2} = \{(a, b)\; |\; (a > b) \lor (a = b - 1)\}$
	$R_{1} \cap R_{2} = \{(a, b)\; |\; (a > b) \land (a = b - 1)\} = \{0\}$
	$R_{1} - R_{2} = \{(a, b)\; |\; (a > b) \land (a \neq b - 1)\}$

Set Composition
	$R(A\; to\; B)\; and\; S(B\; to\; C)$ is the relation
	$R = \{(1, 1), (1, 4), (2, 3), (3, 1), (3, 4)\}$
	$S = \{(1, 0), (2, 0), (3, 1), (3, 2), (4, 1)\}$	
	$S \circ R = \{(a, c)\; |\; a \in A \land c \in C \land \exists b(b \in B \land (a, b) \in R \land (b, c) \in S\}$
	$S \circ R = \{(1, 0), (1, 1), (2, 1), (2, 2), (3, 0), (3, 1)\}$


---

**Hasse Diagram :**
A **Hasse diagram** is a graphical representation of a **partially ordered set (poset)** that illustrates the order relation between elements in a simplified and intuitive way. It is specifically designed to highlight the **direct relationships** between elements by omitting redundant information such as reflexive and transitive edges.

Given a poset $(P,\; ≤)$, where $P$ is a set and $≤$ is a partial order:
1. The elements of $P$ are represented as **nodes**.
2. An edge (line) is drawn from node $a$ to node $b$ if:
    - $a\;≤\;b$ (i.e., $a$ is less than or equal to $b$).
    - There is no intermediate $c \in P$ such that $a\;≤\;c\;≤\;b$(this ensures transitive edges are omitted).
3. Nodes are arranged so that if $a\; ≤\; b$, then $b$ is **placed above** $a$ in the diagram.

Properties of a Hasse Diagram
1. **Reflexive relations** $(a \leq a)$ are not explicitly shown.
2.  **Antisymmetric relations** $(a \leq b \land b \leq a$ imply $a=b)$ ensure no loops in the diagram.
3.  **Transitive edges are omitted** for clarity.

