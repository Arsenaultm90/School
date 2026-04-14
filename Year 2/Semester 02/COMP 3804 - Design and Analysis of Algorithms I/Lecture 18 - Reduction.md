At its core, reduction is a way of saying: **"Problem A is at least as hard as Problem B"** — by showing that if you can solve A, you can automatically solve B.

To prove $P \not \in NP$, we need $L$ such that $L \in NP$ and $L \not \in P$.

More formally: **reducing problem B to problem A** means writing an algorithm that:
1. Takes an instance of B
2. Transforms it into an instance of A
3. Solves A
4. Translates the answer back to an answer for B

If this transformation takes polynomial time, we call it a **polynomial-time reduction**, written **B ≤ₚ A** (read: "B reduces to A" or "B is poly-time reducible to A").

#### How It Is Used
Reduction lets you reason about **hardness** without re-inventing the wheel:
- If **B ≤ₚ A** and A is easy (in P) → B is also easy
- If **B ≤ₚ A** and B is hard (NP-hard) → A is _at least_ as hard as B

This is how NP-completeness works. To show a new problem X is NP-complete, you:
1. Show X is in NP (a solution can be verified in polynomial time)
2. Take a _known_ NP-complete problem and reduce it to X
![[Pasted image 20260407082059.png]]


---
## The "Oracle" Mindset

When doing reductions, imagine you have a **magic black box (oracle)** that solves problem A instantly. Your job is just to:
- Encode your problem B into A's language
- Ask the oracle
- Decode the result

You're not implementing A, you're _assuming_ it's solved, and using that to solve B.

##### **Example: 3-SAT ≤ₚ Independent Set**
This is a classic textbook reduction used to prove Independent Set is NP-complete.

**3-SAT**: Given a boolean formula in Conjunctive Normal Form with 3 literals per clause, is there an assignment making it true? 
**Independent Set**: Given a graph G and integer k, is there a set of k vertices with no two connected by an edge?

**The reduction**:
For each clause (e.g. `x₁ ∨ ¬x₂ ∨ x₃`), create a **triangle** of 3 nodes, one per literal. Then add edges between **contradictory literals** across clauses (e.g. connect node `x₁` in one clause to node `¬x₁` in another).

Set k = number of clauses.

**Why it works**:
- Picking one node per triangle = choosing one literal to be true per clause
- The "contradiction edges" ensure you never pick `x₁` and `¬x₁` simultaneously
- So an independent set of size k ↔ a satisfying assignment of the formula

This shows that if you could solve Independent Set in polynomial time, you could solve 3-SAT in polynomial time, which would mean P = NP.

![[Pasted image 20260407084315.png]]
**Step 1** — Each clause becomes a triangle. The triangle edges mean you can only pick _one_ node per triangle (any two nodes in the same triangle are adjacent).
**Step 2** — Red dashed conflict edges connect every literal to its negation across triangles. These prevent contradictory choices.
**Step 3** — The valid independent set is highlighted. Notice no two green nodes share an edge (neither a triangle edge nor a conflict edge).



---
## Languages L, L'

$L \leq_{p} L'$
	$L$ is polynomial-time reducible to $L'$
	$L'$ is at least as difficult as $L$

$\exists$ function $f$:
	1. $f$: input $x$ to $L$ $\rightarrow$ input $f(x)$ to $L$
	2. $x \in L \iff f(x) \in L'$
	3. Time to compute $f(x): O(|x|^c)$

$A'$: Algorithm for $L'$
How to solve $L$:
	Input $x$
	Compute $f(x)$
	Run $A'(f(x))$


#### Examples
**Clique & Independent Set**
Clique = {(G, K) : Graph G has a clique with 'K' vertices }
Independent Set = {(G, K) : Independent Set }

G = (V, E)
clique : $V' \subset V$,  $\forall \space u, v \in V'$ : {$u, v$} $\in E$
independent set : $V' \subset V$, $\forall$ $u, v \in V', u \neq v$ : {$u, v$} $\not \in E$

![[Clique 1.png]]
{4, 5, 6, 7} : clique of size 4
{1, 4, 10} : independent set of size 3

Claim: Clique $\leq_{p}$ Independent Set
To prove this we need function $f$:
	1. $f: \underset{\text{input to Clique}}{(G, K)} \rightarrow \underset{\text{input to Indep Set}}{(G', K')}$
	2. $G$ has a clique of size $K \iff G'$ has independent set of size $K'$
	3. Time to construct $(G', K')$:
		Polynomial length of $(G, K)$

$f(G, K) = (\overline{G}, K)$
$\overline{G}$ : in $G$, replace each edge by non-edge and each non-edge by edge
	 If {u, v} **∈ E** (edge exists in G) → {u, v} **∉ Ē** (no edge in Ḡ)
	If {u, v} **∉ E** (no edge in G) → {u, v} **∈ Ē** (edge in Ḡ)
![[Screenshot 2026-04-12 at 9.49.34 AM.png]]
$V'$ clique of size $K$ in $G \iff V'$ independent set of size $K$ in $\overline{G}$ 



**Vertex Cover**
Vertex Cover = {(G, K) : graph G has vertex cover of size $K$ }
	$V' \subset V$, for each edge {$u, v$} $\in E$:
		$u \in V'$ or $v \in V'$
G = (V, E)

![[VertexCover.png]]
V' = {2, 3, 5, 7} : Vertex Cover

Claim: Clique $\leq_{p}$ Vertex Cover
To prove this we need function $f$:
	1. $f: \underset{Clique}{(G, K)} \rightarrow \underset{Vertex Cover}{(G', K')}$
	2. $G$ has a clique of size $K \iff G'$ has a vertex cover of size $K'$
	3. Time to compute $(G', K')$:
		Polynomial in length of $(G, K)$

$f(G, K)$ = ($\overline{G}, n - K$), $n$ = # of vertices of $G$
Assume $G = (V, E)$ has a clique $V'$ of size $K$
We can show $V$ \ $V'$  is Vertex Cover in $\overline{G}$

Arbitrary edge {$u, v$} in $\overline{G}$
To show $u$ or $v$ in $V$ \ $V'$
Assume not. Then $u$ and $v$ in $V'$.
Since $V'$ is a clique in $G$: {$u, v$} is an edge in $G$.
	∴ {$u, v$} is not an edge in $\overline{G}$



**Boolean Formula**
Variables : $x_{1}, \dots, x_{n}$
$\varphi = C_{1}, \dots, C_{n}$ (Clause = $C_{i}$)
$C_{i} = \ell^i_{1} \lor \ell_{2}^i \lor \ell^i_{3}$
$\ell^i_{j}$ : Literal (variable or negation of variable)
Satisfiable if $\exists$ truth values for $x_{1}, \dots, x_{n}$ such that $\varphi$ = true

3SAT = { $\varphi : \varphi$ is as above, $\varphi$ is satisfiable }
	$\hookrightarrow$ 3 literals in each clause

Independent Set = {($G, K$) : Graph $G$ has an independent set of size $K$}

Claim : 3SAT $\leq_{p}$ Independent Set

We need function $f$ :
	1. Boolean formula $\varphi \rightarrow (G, K)$
	2. $\varphi$ satisfiable $\iff G$ has an independent set of size $K$
	3. Time to compute ($G, K$) is $O(|\varphi|^c)$

$G$ has 3m vertices; One vertex for each literal
for every clause $C_{i} = \ell^i_{1} \lor \ell^i_{2} \lor \ell^i_{3}$

![[3SAT.png]]

$K = m =$ # of clauses

$\varphi = \underset{C_{1}}{(\lnot x_{1} \lor x_{2} \lor \lnot x_{3})} \land \underset{C_{2}}{(x_{1} \lor \lnot x_{2} \lor x_{3})} \land \underset{C_{3}}{(x_{1} \lor x_{2} \lor x_{3})}$
	$m = 3$

![[Boolean.png|500]]

$x_{1} = F$
$x_{2} = T$
$x_{3} = T$

We choose one vertex in each clause that equates to $TRUE$ to create the independent set.
This is to say, if we can find an independent set in the graph, then the 3SAT is satisfiable.




**3Colour**
3Colour = {$G$ : graph $G$ has 3-colouring}
Each vertex gets "colour" 1, 2, or 3.
for each edge {$u, v$} : $u$ and $v$ different colours
![[3Colour.png]]

Claim : 3Colour $\leq_{p}$ 3SAT
We need function $f$:
	1. $f: G \rightarrow \varphi$
	2. $G$ has 3-Colouring $\iff \varphi$ is satisfiable
	3. Time to compute $\varphi$ : $O(|G|^c)$

$G = (V, E)$, $V =$ {$v_{1}, \dots, v_{n}$}
Variables  $x_{i, c}$ , $1 \leq i \leq n$, $1 \leq c \leq 3$

Idea: $x_{i, c}$ = True $\iff$ Vertex $v_{i}$ has Colour $c$
Vertex $v_{i}$ gets exactly one colour:
	$x_{i_{1}}, x_{i_{2}}, x_{i_{3}} = TRUE \iff v_{i}$ has $\geq$ 1 colour $$[\space \underset{v_{i} \space has \geq 1 \space colour}{(x_{i_{1}} \lor x_{i_{2}} \lor x_{i_{3}})} \space ] \land [\space \underset{v_{i} \space has \leq 1 \space colour}{(\lnot x_{i_{1}} \lor \lnot x_{i_{2}}) \land (\lnot x_{i_{1}} \lor \lnot x_{i_{3}}) \land (\lnot x_{i_{2}} \lor \lnot x_{i_{3}})} \space]$$

edge {$v_{i}, v_{j}$} : $v_{i}$ and $v_{j}$ different colours:
	$x_{i_{1}} \land x_{j_{1}} = TRUE$ : $v_{i}$ and $v_{j}$ both colour 1
	∴ 	$x_{i_{1}} \land x_{j_{1}}$ must be $FALSE$
	∴ $\lnot(x_{i_{1}} \land x_{j_{1}})$ must be $TRUE$
	DeMorgan $\lnot x_{i_{1}} \lor \lnot x_{j_{1}}$ $$\underset{v_{i} \space and \space v_{j} \text{ have different colours}}{(\lnot x_{i_{1}} \lor \lnot x_{j_{1}}) \land (\lnot x_{i_{2}} \lor \lnot x_{j_{2}}) \land (\lnot x_{i_{3}} \lor \lnot x_{j_{3}})}$$

Final Boolean Expression: $$[\space \underset{v_{i} \space has \geq 1 \space colour}{(x_{i_{1}} \lor x_{i_{2}} \lor x_{i_{3}})} \space ] \land [\space \underset{v_{i} \space has \leq 1 \space colour}{(\lnot x_{i_{1}} \lor \lnot x_{i_{2}}) \land (\lnot x_{i_{1}} \lor \lnot x_{i_{3}}) \land (\lnot x_{i_{2}} \lor \lnot x_{i_{3}})} \space]$$ $$\land$$
$$\underset{v_{i} \space and \space v_{j} \text{ have different colours}}{(\lnot x_{i_{1}} \lor \lnot x_{j_{1}}) \land (\lnot x_{i_{2}} \lor \lnot x_{j_{2}}) \land (\lnot x_{i_{3}} \lor \lnot x_{j_{3}})}$$






---
## Summary

When you have a new problem X and want to prove it's NP-hard, you need to find a known NP-hard problem Y and show Y ≤ₚ X (reduce _from_ Y _to_ X). This proves X is at least as hard as Y.

| Problem                                      | NP Problem                         |
| -------------------------------------------- | ---------------------------------- |
| Choosing a subset that satisfies constraints | 3-SAT or Subset Sum                |
| Graph connectivity / paths / cycles          | Hamiltonian Path or 3-colorability |
| Covering everything with few resources       | Vertex Cover or Set Cover          |
| Packing as much as possible                  | Independent Set or Clique          |
| Scheduling / ordering tasks                  | 3-SAT or Partition                 |

**1. Does my problem have a "yes/no structure" based on a subset or assignment?** → Try 3-SAT. It's the most versatile starting point because logical constraints can encode almost anything.

**2. Does my problem live on a graph?** → Try Hamiltonian Path/Cycle (if it's about visiting things), Vertex Cover (if it's about selecting nodes to cover edges), or 3-Colorability (if it's about assigning categories without conflicts).

**3. Does my problem ask "can we fit things into bins/groups with a budget?"** → Try Subset Sum or Partition. These are the workhorses for numeric/resource problems.


