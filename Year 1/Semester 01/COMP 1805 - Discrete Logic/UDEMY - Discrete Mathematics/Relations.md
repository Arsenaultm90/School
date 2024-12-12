
---

##### The Language of Relations
We define a relation between sets as $R$.
$R$ can be defined as a condition on the cartesian product of the two sets, resulting in a set of values that meet the conditions of the relation.

Ex.$$\displaylines{A=\{1, 2, 3\}\\
B=\{2, 3, 4, 5\}\\
}$$
We can say:
	$x$ is related to $y$, if and only if, $x<y$.
	$x\;R\;y$, where R = $x<y$

$$\displaylines{\text{Resulting Set}\\
\{(1,2), (1,3), (1,4), (1,5), (2,3), (2,4), (2,5), (3,4), (3,5)\}}$$


---
##### Relation On Sets
A relation $R$ from $A$ to $B$ is a subset of $A \times B$. 
Given an ordered pair $(x, y)$ in $A\times B$, $x$ is related to $y$ by $R$, written $x\;R\;y$, if, and only if, $(x, y)$
is in $R$. 

$A$ is the **Domain**.
$B$ is the **Codomain**.


---
##### The Inverse of a Relation
Let $R$ be a relationship from $A$ to $B$. Define the inverse relation $R^{-1}$ from $B$ to $A$ as follows:
	$R^{-1} = \{(y,x) \in B\times A\;|\;(x,y) \in R\}$

Ex.$$\displaylines{A=\{2, 3, 4\}\\
B=\{5, 6, 8\}\\ \\
x\;R\;y \Leftrightarrow x|y\\
R=\{(2,6), (2,8),(3,6),(4,8)\}\\
R^{-1} = \{(6,2),(8,2),(6,3),(8,4)\}}$$

---
##### Reflexivity, Symmetry, and Transitivity
Describes the relation that the elements of a set have to each other.

**Reflexivity**
	A relation $R$ on a set $A$ is **reflexive** if, for every element $a \in A$, the pair $(a,a)$ is in the relation $R$. $$\forall a \in A,\; (a, a) \in R$$
**Symmetry**
	A relation $R$ on a set $R$ is **symmetric** if, whenever an element $a$ is related to an element $b$, then $b$ is also related to $a$. $$\forall a,b \in A,\;if\;(a,b) \in R,\; then (b,a) \in R$$
**Transitivity**
	A relation $R$ on a set $A$ is **transitive** if, whenever $a$ is related to $b$ and $b$ is related to $c$, then $a$ is also related to $c$. $$\forall a, b, c \in R,\;if\;(a,b) \in R,\;and\;(b,c) \in R,\;then\; (a,c)\in R$$

---
