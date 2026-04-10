**P**  = {All problems solvable in polynomial time} 

**NP** = {Decision Problems solvable in non-deterministic polynomial time} (YES or NO)
	A problem is in **NP** if:
		Given a _candidate solution_, you can **verify it quickly** (in polynomial time)

**NP-Hard**
A problem is **NP-hard** if:
	Every problem in NP can be reduced to it

- It is **at least as hard as the hardest problems in NP**
- It might be:
    - in NP
    - or _even harder_ (not in NP)

**NP-Complete** = {hardest problems that are still verifiable quickly}
A problem is **NP-complete** if:
1. In NP
2. NP-hard


---
#### NP
X is NP-Complete if X$\epsilon$NP AND X is NP-Hard
X is NP-Hard if every problem Y$\epsilon$NP reduces to X

![[Screenshot 2026-04-09 at 9.11.23 AM.png]]
(Not accurate, just a representation)
- **P** — problems solvable in polynomial time
- **NP** — problems where solutions are _verifiable_ in polynomial time (P is a subset of NP)
- **NP-Complete** — the hardest problems inside NP, sitting right at the boundary
- **NP-Hard** — at least as hard as NP-Complete, but not necessarily inside NP


---
## How To Prove Y is NP-Complete

1. Prove $Y \epsilon NP$
	1. Non-Deterministic Algorithm
	2. Certificate + Verify
2. Reduce from known NP-Complete problem $Y$ to $X$


#### NP-Complete Problems 

|Problem|Pattern|
|---|---|
|3-SAT|logical constraints|
|Independent Set|no conflicts|
|Vertex Cover|covering constraints|
|Clique|all-to-all compatibility|
|Hamiltonian Cycle|path/ordering|
|Subset Sum|numeric selection|


---
## Language

Language of a decision problem:
	Set of all inputs for which the answer to the question is YES

**Example:**
Hamilton Cycle = {G: G is a graph that has a Hamilton Cycle}
	If GGG has a Hamiltonian cycle → include it in the set
	If not → don’t include it

#### P : Polynomial Time
Language L is in P if:
	$\exists$ algorithm A , $\exists$ integer c $\geq$ 1:

for every input x:
	if $x \in L$: A(x) returns YES
	if $x\not\in L$: A(x) returns NO
	Running time of A(x) is O($|X|^c$)
		|X| = length of x


#### NP : Non-Deterministic Polynomial Time
Language L is in NP if:
	$\exists$ algorithm V (verification, takes 2 inputs)
	$\exists$ constant c $\geq$ 1

for every input x:
	$x \in L \iff \exists$ proof/certificate 'y' such that
		|y| = $O(|x|^c)$
		V(x, y) returns YES
		Running time of V(x, y) is polynomial in |x|



---
## Examples Of NP Problems

#### 3SAT
Given a boolean formula in the form: $$(x_{1} \lor x_{2} \lor \bar{x_{3}}) \land (\bar{x_{2}} \lor x_{3} \lor \bar{x_{7}})$$
Literals = $x_{1}$ or $\bar{x_{1}}$
Clauses = $(x_{1} \lor x_{2} \lor \bar{x_{3}})$

Can you set the variables to either T or F such that the formula = True

$\epsilon$NP :
	guess $x_{1}$ = T or F
	guess $x_2$ = T or F
	...
	check if formula is T or F:
		T = Return YES
		F = Return NO


#### Hamilton Cycle
**Input:** Undirected Graph G
**Question:** Does G have a Hamilton Cycle? (Cycle visits every vertex at least once)
Not known to be in P

**It is in NP:**
	Proof/Certificate: Sequence $v_1, v_{2}, \dots, v_{n}$ of vertices 

**Verify:** 
	Check if {$v_{1}, \dots, v_{n}$} = vertex set of G
	Check if {$v_{1}, v_{2}$}, {$v_{2}, v_{3}$}, ..., {$v_{n}, v_{1}$} are edges


#### Travelling Salesman Problem
**Input:** nxn matrix C of integers
	Integer K
**Question:** Is there a cycle that visits every city and has a total cost $\leq$ K?
Not known to be in P

**Is it in NP:**
	Cities are $1, \dots, n$

**Proof/Certificate:**
	Permutation 
	$\pi_{1}, \dots, \pi_{n}$ of $1, \dots, n$

**Verify:**
	Check if {$\pi_{1}, \dots, \pi_{n}$} = {$1, \dots, n$}
	Check if $\sum^{n-1}_{i=1} C_{\pi_{i}, \pi_{i+1}} + C_{\pi_{n}, \pi_{1}}$


#### Subset Sum
**Input:** Set S of integers,
	Integer t

**Question:** Is there a subset T of S such that $\sum_{x \epsilon T} x = t$?
Not known to be in P
It is in NP

**Proof/Certificate:** 
	Set T

**Verify:**
	Check if $T \subset  S$
	Check if $\sum_{x \epsilon T} x = t$



#### Clique
**Input:** Undirected graph G,
	Integer k

**Question:** Does G have a clique of size K? (Complete subgraph with K vertices)
Not known to be in P
It is in NP

**Proof/Certificate:**
	Vertex set U

**Verify:**
	Check if $U \subset$ vertex set G
	Check if |U| = K
	Check if for all x,y in U, x$\neq$y:
		{x,y} is an edge in G

