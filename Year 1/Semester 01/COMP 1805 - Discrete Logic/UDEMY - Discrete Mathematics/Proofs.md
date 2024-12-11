##### Terminologies
**Conjecture:**
	A statement that is being proposed to be **True**.

**Theorem:**
	A statement that can be shown to be **True**.

**Axioms(or Postulates):**
	Statements we assume to be **True**.

**Lemma:**
	A smaller component of a **Theorem** that we can prove individually.

**Corollary:**
	A **Theorem** that can be established directly from a proven **Theorem**.

---

##### Direct Proofs
A proof that utilizes existing proven theorems, axioms, and lemmas to prove your statement.

Ex. 
If $n$ is odd, then $n^2$ is an odd number.
$$\displaylines{n =2k+1\\
n^2 = (2k+1)^2\\
n^2 = 4k^2 + 4k + 1\\
n^2 = 2(2k^2 + 2k) + 1\\
b = 2k^2 + 2k\\
n^2 = 2(b) + 1}$$
---

##### Proof By Contrapositive - Indirect Proof
The Contrapositive allows us to reverse and negate the hypothesis and conclusion to better handle a proof where the conclusion is easier to prove. 

Logical Equivalence: $p \rightarrow q \equiv \neg q \rightarrow \neg p$

**Ex 1.**
For $n \in ℤ$, if $n^2$ is odd, then $n$ is odd.
	$\forall n \in ℤ\;(n^2 = 2k+1) \rightarrow (n = 2k+1)$

Since it is much more difficult to prove this one directly, we can implement the **Contrapositive** as our assumption where, $$\displaylines{p=n^2\;is\;odd\\q=n\;is\;odd\\ p \rightarrow q \equiv \neg q \rightarrow \neg p}$$
Now we can more easily prove that,
For $n \in ℤ$, if $n$ is even, then $n^2$ is even.
	$\forall n \in ℤ\;(n = 2k) \rightarrow (n^2 = 2k)$
$$\displaylines{n = 2k\;\;\;Initial Assumption\\
n^2 = (2k)^2\\
n^2 = 4k^2\\
n^2 = 2(2k^2)\\
a = 2k^2\\
n^2 = 2a\;\;\;Definition\;of\;Evenness}$$



**Ex 2.**
For $n,m \in ℤ^+$, if $n·m$ is greater than 100, then $n > 10$ or $m > 10$.
	$\forall n,m \in ℤ^+\;(n·m > 100) \rightarrow (n>10 \lor m>10)$

$$\displaylines{p = n·m > 100\\ q=n>10 \lor m>10\\
p \rightarrow q \equiv \neg q \rightarrow \neg p}$$
Now we have,
If $n \leq 10 \land m \leq 10$, then $n·m \leq 100$
	$\forall n,m \in ℤ^+\;(n \leq 10 \land m \leq 10) \rightarrow (n·m \leq 100)$
$$\displaylines{n \leq 10\\
n·m \leq 10·m\\
m \leq 10\\
10·m \leq 100\\
n·m \leq 100}$$



**Ex 3.**
If $4^n - 1$ is a prime, then $n$ is odd.
	$\forall n \in ℤ^+\;(4^n-1=\;'p') \rightarrow (n = 2k+1)$
$$\displaylines{p = (4^n-1 =\;'p')\\
q = (n = 2k+1)\\
p \rightarrow q \equiv \neg q \rightarrow \neg p}$$
Now we have,
If $n$ is even, then $4^n-1$ is a $\text{Composite}$.
	$\forall n \in ℤ^+\;(n = 2k) \rightarrow (4^n-1 =\;'c')$
$$\displaylines{4^{2k}-1 = (4^k-1)(4^k+1)}$$
Given the difference of squares, we can see that $4^n \pm 1$ will always be greater than $1$. 
With the definition of prime numbers stating that they must not be $1$ and may only contain the divisors of $1$ and itself, this proves that we will have values other that $1$ and the number as divisors.

---

##### Proof By Contradiction - Indirect Proof
Prove a statement by assuming the opposite is **True**. Should we arrive that it is in fact **False**, then we have proven, by **Contradiction**, that the original statement is **True**.

$$\displaylines{
p \rightarrow q  \begin{aligned}\quad \begin{array}{c}
\text{Contradiction} \\ \Longrightarrow
\end{array} \end{aligned}\quad \neg(p \rightarrow q) \\ ------------------ \\
p \rightarrow q \equiv \neg p \lor q\\
\neg(\neg p \lor q)\\
p \land \neg q}$$

With the proposition now in a **Conjunctive** form, we can separate the pieces using **Simplification**.
The goal will be to arrive at a statement that contradicts our initial hypothesis. 
We can then use **Conjunction** to create our full contradictory proposition allowing us to use **Complements Law** to arrive at a value of **False**.

---

##### Exhaustion Proofs (Proof By Case)
Prove the proposition by separating it into smaller cases and proving those individually.

Ex.
Prove that $(n+1)^3 \geq 3^n$ for $n \in ℕ$ and $n \leq 4$.
$$\displaylines{n =1\quad \Longrightarrow \quad(1+1)^3 = 2^3 \geq 3^1 = 8 \geq 3\\
n = 2\quad \Longrightarrow \quad (2+1)^3 = 3^3 \geq 3^2 = 27 \geq 9\\
n = 3 \quad \Longrightarrow \quad (3 + 1)^3 = 4^3 \geq 3^3 = 64 \geq 27\\
n = 4 \quad \Longrightarrow \quad (4 = 1)^3 = 5^3 \geq 3^4 = 125 \geq 81}$$
We can see in our four cases above, that $(n+1)^3$ was larger than $3^n$ in every case.

---

##### Proofs By Induction
1. Show that $P(a)$ is **True**.
2. Show that for all integers $k \leq a$, if $P(k)$ is **True**, then $P(k+1)$ is **True**. 

Ex.
$1+2+3+...+n = \frac{n(n+1)}{2}$ for $n \in ℤ\;|\;n \geq 1$
$$\displaylines{\\ \text{Base Case}\\
n = 1\\
\frac{1(1+1)}{2} = 1\\ \\ \\
\text{Inductive Case}\\
\text{Inductive Hypothesis: } 1+2+3+\dots+k = \frac{k(k+1)}{2}\\ \\
1 + 2 + 3 +\dots + (k+1)= \frac{(k+1)((k+1)+1)}{2}\\ \\
\begin{aligned} &\text{LHS: } \left\{ \begin{aligned} &1 + 2 + 3 + \dots + k = \frac{k(k+1)}{2} \\ \\ &\frac{k(k+1)}{2} + (k+1) \\ \\ &\frac{k^2 + k}{2} + \frac{2(k+1)}{2} \\ \\ &\frac{k^2 + 3k + 2}{2}\end{aligned} \right. \end{aligned} \\ \\
\begin{aligned} &\text{RHS: } \left\{ \begin{aligned} &\frac{(k+1)((k+1)+1)}{2} \\ \\
&\frac{(k+1)(k+2)}{2}\\ \\
&\frac{k^2 + 3k + 2}{2} &&&
\end{aligned} \right. \end{aligned} \\ \\
\text{LHS} = \text{RHS} \\
\frac{k^2+3k+2}{2} = \frac{k^2+3k+2}{2}
}$$
