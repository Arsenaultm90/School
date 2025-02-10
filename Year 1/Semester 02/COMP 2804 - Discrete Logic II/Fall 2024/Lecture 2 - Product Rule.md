Define a set $S$ and determine $|S|$.
	$|S|$ : Size of $S$


---
##### The Rule of Sum
If a task can be done either one of $n_1$ ways or in one of $n_2$ ways, where the two sets of ways are **disjoint**, then there are $n_1 + n_2$ ways to complete a task.

**Disjoint :** Two sets with no element in common. Intersection is empty.

Example:
If we roll two dice, a green die and a red die, how many ways can we make 7 or 11?

Sum of $7 : (1, 6), (6, 1), (2, 5), (5, 2), (3, 4), (4, 3)$ 
Sum of $11 : (5, 6), (6, 5)$

So we have 6 ways to get 7 and 2 ways to get 11. 
∴ We have 6 + 2 = 8 ways to get a sum of 7 or 11.


---
##### Product Rule
If a procedure, $P$, has $m$ steps, and for each $\text{i} \in \{1, \dots, m\}$, the number of ways to execute step $i$ is $N_{i}$, then the number of ways to execute $P$ is $N_1 \times N_{2} \times \dots \times N_{m}$.

If $P$ generates elements from a set $S$ and
	(onto) For each $x \in S$, there is an execution of $P$ that generates $x$.
	(one-to-one) Any two different executions of $P$ generate distinct elements of $S$
Then...
	$|S| = N_{1} \times N_{2} \times N_{3} \times \dots \times N_{m}$ 

**Example:**
Drink: Coke/Beer
Food: Burger/Club Sandwich/Chicken Sandwich

Step 1: Choose a drink(Coke, Beer)
	$N_{1}$ = 2

Step 2: Choose a meal(Burger/Club Sandwich/Chicken Sandwich)
	$N_{2}$ = 3

OR

Coke -> 3 Options
Beer -> 2 Options

∴ Total number of ways this procedure can be executed is 
	$3 · 2 = 6$

**Example:**
A bitstring is a sequence of $0$'s and $1$'s.
$S_{n}$ : The set of all bitstrings of length $n$, where integer $n \geq 0$.

$$\displaylines{S_{3} = \{000, 001, 010, 011, 100, 101, 110, 111\}\\ \\
\text{for}\; i \leftarrow 1\; \text{to}\;n,\\
\text{write down the value of}\; b_{i} \in \{0, 1\}\\ \\
\; n\; \text{steps}\\
\; N_{1} = 2, \; N_{2} = 2,\; N_{3} = 2, \dots, N_{n}\\ \\
N_{1} \times N_{2} \times N_{3} \times \dots \times N_{n}\\
2 \times 2 \times 2\times \dots = 2^n\\
∴\;|S| = 2^n}$$


---
##### Counting Functions
The number of functions between two sets. $$\displaylines{|A| = m,\; |B| = n\\n^m}$$

---
**One-To-One Functions**
The number of one-to-one functions between two sets can be determined using the following.
$$\displaylines{f : A \rightarrow B \\ \\
\text{Case 1} \\
\text{If } m > n, \text{then the number of One-To-One functions is : } 0
\\ \\
\text{Case 2}\\
\text{If } n > m, \text{then the number of One-To-One functions is : }
n ·(n-1)·(n-2)·{\dots}·n-m+1 \\
\text{Simplify : }n ·(n-1)·(n-2)·{\dots}·n-m+1 · \frac{(n-m)·(n-m-1)·{\dots}·1}{(n-m)·(n-m-1)·{\dots}·1} \\
\text{ Which gives us:}\; \frac{n!}{(n-m)!}\\ \\
\text{Case 3}\\
\text{If } n = m, \text{then it becomes } n!}$$

Example: $$\displaylines{A = \{1, 2, 3\}\\
B=\{a, b, c, d, e\}\\ \\
\frac{5!}{(5-3)!} = \frac{5!}{2!} = \frac{120}{2} = 60}$$

---
##### Extras

**Factorial**
$$\displaylines{n! = \begin{cases} 1 \cdot 2 \cdot 3 \cdot {\dots} \cdot n = n \cdot (n-1) \cdot (n-2) \cdot {\dots} \cdot 1, & \text{if} \; n \geq 1 \\ 1, & \text{if} \; n = 0 \end{cases}}$$


**Permutations** - Order matters
$$\displaylines{\text{Repetition is NOT allowed :} \\ P\binom{n}{r} = \frac{n!}{(n-r)!}\\ \\
\text{Repetition is allowed :} \\
n^r}$$

**Combinations** - Order doesn't matter
$$\displaylines{\text{Repetition is NOT allowed :} \\ C\binom{n}{k} = \frac{n!}{k!(n-k)!} \\ \\
\text{Repetition is allowed :} \\
C\binom{n+r-1}{r-1}= C(n, r)=\frac{n!}{r!(n-r)!}}$$


**Permutations**: Use when **order matters** (e.g., arranging, ranking, assigning positions).
**Combinations**: Use when **order does not matter** (e.g., selecting, choosing, forming groups).

