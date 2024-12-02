#### Logical Equivalency Laws
 
 **1. Identity Laws**
$\displaylines{p∧True≡p \\ p∨False≡p}$

---
 **2. Domination Laws**
$\displaylines{p∨True≡True \\ p∧False≡False}$

---
**3. Idempotent Laws**
$\displaylines{p∨p≡p \\ p∧p≡p}$

---
**4. Double Negation Law**
${¬(¬p)≡p}$

---
**5. Complement Laws**
${p∨¬p≡True \\ p∧¬p≡False}$

---
**6. Commutative Laws**
$\displaylines{p∨q≡q∨p \\ p∧q≡q∧p}$

---
**7. Associative Laws**
$\displaylines{(p∨q)∨r≡p∨(q∨r) \\ (p∧q)∧r≡p∧(q∧r)}$

---
 **8. Distributive Laws**
$\displaylines{p∨(q∧r)≡(p∨q)∧(p∨r) \\ p∧(q∨r)≡(p∧q)∨(p∧r)}$

---
 **9. De Morgan's Laws**
$\displaylines{¬(p∧q)≡¬p∨¬q \\ ¬(p∨q)≡¬p∧¬q}$

---
 **10. Absorption Laws**
$\displaylines{p∨(p∧q)≡p \\ p∧(p∨q)≡p}$

---
**11. Negation of True and False**
$\displaylines{¬True≡False\\\ ¬False≡True}$

---
**12. Implication Law**
${p→q≡¬p∨q}$

---
**13. Biconditional Law**
${p↔q≡(p→q)∧(q→p)}$

---

#### Inference Laws

**1. Modus Ponens (Law of Detachment)**
$\displaylines{p→q, p\\ ∴q}$

---
 **2. Modus Tollens**
$\displaylines{p→q,  ¬q \\ ∴¬p}$

---
 **3. Hypothetical Syllogism**
$\displaylines{p→q,  q→r \\∴p→r}$

---
**4. Disjunctive Syllogism**
$\displaylines{p∨q,  ¬p \\ ∴q}$

---
 **5. Addition**
$\displaylines{p \\ ∴p∨q}$ 

---
**6. Simplification**
$\displaylines{p∧q \\ ∴p}$

---
**7. Conjunction**
$\displaylines{p,  q \\∴p∧q}$

---
 **8. Resolution**
$\displaylines{p∨q,  ¬p∨r \\∴q∨r}$

---
**9. Constructive Dilemma**
$\displaylines{(p→q)∧(r→s),  p∨r \\∴q∨s}$

---
**10. Destructive Dilemma**
$\displaylines{(p→q)∧(r→s),  ¬q∨¬s \\∴¬p∨¬r}$

---
**11. Universal Instantiation**
$\displaylines{∀x  P(x)\\∴P(c)}$

---
 **12. Existential Instantiation**
$\displaylines{∃x  P(x)\\∴P(c)}$

---
 **13. Universal Generalization**
$\displaylines{P(c)\\∴∀x  P(x)}$

---
 **14. Existential Generalization**
$\displaylines{P(c) \\∴∃x  P(x)}$

---
 **15. Law of Contrapositive**
$\displaylines{p→q \\∴¬q→¬p}$


#### Predicate Logic
A **predicate** is a statement or function that expresses a property or relation that can be evaluated as **true** or **false** depending on the values of its variables.

**Components of a Predicate:**
1. **Predicate symbol**: A letter or symbol representing the predicate.
2. **Variables(Atomic Predicate)**: The subject(s) that the predicate applies to.
3. **Arguments**: The actual values or objects that replace the variables.

Atomic predicates will never represent the negation of an argument.

**Example of a Predicate:**
- Let P(x) represent the predicate "x is a prime number."
- P(5) is **true** because 5 is a prime number.
- P(4) is **false** because 4 is not a prime number.
	Here, P(x) is a **predicate**, and x is a **variable**. The truth value of P(x) depends on the value assigned to x.

**Example of Multiple Variables In A Predicate:**
Ǝx ∀y (x + y > 2)
"there exists an x such that every y satisfies the expression 𝑥 + 𝑦 > 2"

∀x ∀y Likes(x, y)
“Everybody likes Everybody”

Ǝx Ǝy Likes(x, y)
“Somebody likes Somebody”

∀x Ǝy Likes(x, y)
“Everybody likes at least one person”

Ǝx ∀y Likes(x, y)
“At least one person likes Everybody”

Ǝy ∀x LIkes (x, y)
“At least one person is liked by Everybody”

∀y Ǝx  Likes(x, y)
“Everybody has at least one person who likes them”

#### Arguing w/ Quantified Predicates
Existential Instantiation **_BEFORE_**  Universal Instantiation

**Given Premises:**
"Some students have not taken the course before."
∃𝑥 𝑆(𝑥) ∧ ¬𝐶(𝑥)

"Everyone in this course will learn some discrete math."
∀𝑥 𝑆(𝑥) → 𝐿(𝑥)

**Prove:**
"Someone who learns some discrete math will not have taken this course before."
∃𝑥 𝐿(𝑥) ∧ ¬𝐶(𝑥)

1. ∃𝑥 𝑆(𝑥) ∧ ¬𝐶(𝑥)
2. ∀𝑥 𝑆(𝑥) → 𝐿(𝑥)
3. 𝑆(𝑦) ∧ ¬𝐶(𝑦) (1), Existential Instantiation
4. 𝑆(𝑦) → 𝐿(𝑦) (2), Universal Instantiation
5. 𝑆(𝑦) (3), Simplification
6. 𝐿(𝑦) (4, 5), Modus Ponens
7. ¬𝐶(𝑦) (3), Simplification
8. 𝐿(𝑦) ∧ ¬𝐶(𝑦) (6, 7), Conjunction
9. ∃𝑥 𝐿(𝑥) ∧ ¬𝐶(𝑥) (8), Existential Generalization

#### Formal Proof Methods
Definition Of Evenness:
𝑛 = 2𝑘

Definition Of Oddness:
𝑥 = 2𝑘 + 1

Definition of Rational:
a = m/n, where m, n 𝜖 ℤ,  n ≠ 0


**Direct Proof**
We start with our assumptions and we use manipulation to get our result.

Ex 1:
If 'x' is an even number, then x2 - 6x + 3 is odd.
```
We want to show that this is equivalent to 2x + 1
P -> Q

Assume: x is even
    x = 2a for some a 𝜖 ℤ (Some 'a' in the integers)

Prove: x2 - 6x + 3 = 2x + 1

x2 - 6x + 3
(2a)2 - 6(2a) + 3
4a2 - 12a + 3
4a2 - 12a + 2 + 1
2(2a2 - 6a + 1) + 1
    Now this is in the form of _2x + 1_, which is the definition of 'Oddness'
    
∴ x2 - 6x + 3 is odd.
```


**Proof By Contraposition**  
P -> Q
⌐Q -> ⌐P

Ex 1:
```
Given an integer a, if a^2 is not divisble by 4, then a is odd.
Assume a = 2x(Even)

a^2 = 4x^2
∴ a2 = 4x is divisible by '4'
```


**Proof by Case (By Exhaustion)**
Evaluate each case of the statement.

Ex 1:
```
Odd + Odd => Even
    (2a + 1) + (2b + 1) 
    2a + 2b + 2
    2(a + b + 1)
    ∴ 2x => Even

Even + Even => Even
    2a + 2b
    2(a + b)
    ∴ 2x => Even
```


    
#### Set Theory
[[Sets]]

#### Graph Theory
Graphs are a form of **Abstract Representation.**
Notation: G = (V, E)
	V - A collection of Vertices(or Nodes) each representing an entity of interest.
	E - Edges(or Lines) connecting the vertices to one another representing the relationship between entities.

##### **Undirected Graph**
Each edge is a set of vertices with cardinality two.
The directionality doesn’t matter so the edges are represented by the vertices it is connected to, stored in a set.

Ex.
$(0)-----------(1)$
G = (V, E)
V = {0, 1}
E = {0, 1}


##### **Directed Graph**
Each edge is a Tuple of vertices with cardinality two.
Directionality matters in this case, therefore we represent the set of edges as tuples.

Ex.
$(0)---->(1)$
G = (V, E)
V = {0, 1}
E = {(0, 1)}

##### **Graph Representation Approaches**
**Adjacent**
Two vertices in a graph are considered adjacent if there is an edge connecting them.

Adjacent To: Two vertices, **_u_** and **_v_**, are connected by an edge. Vertex **_u_** is said to be **_adjacent to_** vertex **_v_**.
Adjacent From: Two vertices, **_u_** and **_v_**, are connected by an edged. Vertex **_v_** is said to be **_adjacent from_** vertex **_u_**

**Simple**
A graph is considered simple if it does not allow vertices to be adjacent to themselves.

##### **Adjacency List**
![[adjacency_list =.png]]

##### **Adjacency Matrix**
![[adjacency_matrix =.png]]

##### **Dense/Sparse**
**Dense**
	Has a High Edge-To-Vertex Ratio
	Matrix (Access efficiency)

**Sparse** 
	Has a Low Edge-To-Vertex Ratio
	List (Space efficiency)

  
##### **Graph Types**
**Complete Graphs**
The edge set has an edge between all possible pairs(Every vertex is connected to every other vertex)
The **_Complete Graph_** on ’_n_’ vertices is denoted as Kn

**Cycle Graphs**
The Edge Set has an Edge Between All Possible Pairs of the Form {𝑣𝑖, 𝑣𝑖+1} for 𝑖 ϵ {1, 𝑛 − 1}, and Edge {𝑣𝑛, 𝑣1}
The **_Cycle Graph_** on ’_n_’ vertices (n ≥ 3) is denoted Cn

**Wheel Graphs**
The **_Wheel Graph_** is the same as the **_Cycle Graph_** with one additional vertex connected to every other vertex.
The **_Wheel Graph_** on ’_n_’ vertices (n ≥ 4) is denoted as Wn

**Bipartite Graph**
A Bipartite Graph 𝐺 = (𝑉, 𝐸) Partitions 𝑉 into 𝑉1 and 𝑉2 such that 𝑉1 ∪ 𝑉2 = 𝑉 and 𝑉1 ⋂ 𝑉2 = ∅
Every Edge has One End in 𝑉1 and One End in 𝑉2 the Complete Bipartite Graph 𝐾𝑚, 𝑛 has Partitions of Size 𝑚 and 𝑛 and Every Element in 𝑉1 is Connected to Every Element of 𝑉2.

  
##### **Additional Graph Properties**
**Degree of A Vertex**
The Degree of a Vertex in an Undirected Graph is the Number of Vertices with which it is Adjacent

The "In Degree" of a Vertex in a Directed Graph is the Number of Vertices that it is "Adjacent From"

The "Out Degree" of a Vertex in a Directed Graph is the Number of Vertices that it is "Adjacent To"


**Chromatic Number**
The chromatic number of a graph is the minimal number of colours needed to colour the vertices in such a way that no two adjacent vertices have the same colour.

Complete Graph : Chromatic Number = n (Number of vertices)
Odd Cycle : Chromatic Number = 3
Even Cycle : Chromatic Number = 2
Wheel : Chromatic Number = Cycle Chromatic Number + 1


#### Sequences, Series, and Sums



Models of Computation

Performance Analysis w/ Mathematics

Big Oh Omega and Theta

Introduction to Functions

Introduction to Relations

Countability

Algorithm Design Considerations