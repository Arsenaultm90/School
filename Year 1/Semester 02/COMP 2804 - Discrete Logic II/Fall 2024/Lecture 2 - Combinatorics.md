Define a set $S$ and determine $|S|$.
	$|S|$ : Size of $S$

##### Product Rule
If a procedure, $P$, has $m$ steps, and for each $\text{i} \in \{1, \dots, m\}$, the number of ways to execute step $i$ is $N_{i}$, then the number of ways to execute $P$ is $N_1 \times N_{2} \times \dots \times N_{m}$.

Example:
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


**One-To-One Functions**
The number of one-to-one functions between two sets can be determined using the following.
$$\displaylines{f : A \rightarrow B \\
0- \text{One-To-One functions if}\; m > n\\
n ·(n-1)·(n-2)·{\dots}·n-m+1}$$

Example: $$\displaylines{A = \{1, 2, 3, 4\}\\
B=\{a, b, c, d, e, f\}\\ \\
1\; \text{can map to any of the 6 options in set B}\\
2\; \text{can map to any of the 5 remaining options in set B}\\
∴\;6 \times 5 \times 4 \times 3 = 360}$$

**Factorial**
$$\displaylines{n! = \begin{cases} 1 \cdot 2 \cdot 3 \cdot {\dots} \cdot n = n \cdot (n-1) \cdot (n-2) \cdot {\dots} \cdot 1, & \text{if} \; n \geq 1 \\ 1, & \text{if} \; n = 0 \end{cases}\\ \\
\text{ Which gives us:}\; \frac{n!}{(n-m)!}}$$

In cases where $m \geq n$, it becomes: $n!$



**Stars and Bars Combinatorics**
$$\frac{(n+m-1)!}{(n-1)!}$$



**Permutations**
$$P(n,r) = \frac{n!}{(n-r)!}$$

**Combinations**
$$C(n,r) = \frac{n!}{r!(n-r)!}$$


**Permutations**: Use when **order matters** (e.g., arranging, ranking, assigning positions).
**Combinations**: Use when **order does not matter** (e.g., selecting, choosing, forming groups).