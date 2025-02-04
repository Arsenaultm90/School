##### Pigeonhole Principle

Let $k \geq 1$ be an integer. If $k+1$  or more objects are placed into $k$ holes, then at least one hole contains at least two objects.

OR

If $A$ and $B$ are sets and $|A|$ > $|B|$, then there is no one-to-one function $f : A \rightarrow B$.


**Example :** 
Simon's Drinking Problem
	Simon drinks at least one beer every day.
	In April, which has 30 days, Simon drank exactly 45 beers.

Claim : 
	There is a sequence of consecutive days in April in which Simon drank exactly 14 beers.

Proof :
$$\displaylines{\text{For each }i \in \{1, \dots, 30\},\;\text{let } a_{i} = \text{the number of beers Simon drank on April } i .\\
a_{1} + a_{2} +\dots+a_{30} = 45 \\
a_{i} \geq 1 \text{, for each } i \in \{1, \dots, 29\}\\ \\
\text{Let } b_{i}=a_{1} + a_{2} +\dots+a_{i} \\
b_{30} = 45 \\
b_{i+1}>b_{i},\; \text{for each } i \in \{1, \dots, 29\}\\ \\
b_{1}, b_{2}, ...,b_{30}, b_{1}+14, b_{2}+14, \dots,b_{30}+14\\
m = 60, n=59\\
\text{Since we have 60 numbers in a range of only 59 possible values, } \\ 
\text{the pigeonhole principle tells us that at least two of these numbers must be equal.} \\ \\
b_{i} = b_{j}+14 \\
b_{i} - b_{j} = 14 \\
\text{Number of days in which Simon drank exactly 14 beers}=a_{j+1},\dots,a_{i}}$$


**Example :** 
Let $a_1, ..., a_n+1$ be a sequence of integers in $\{1, 2, 3, \dots, 2n\}$.
Then there exists $i \neq j$ such that $a_{i}$ divides $a_j$ ($a_{i}\div a_{j} = \text{an integer}$).

Write each $a_{i}$ as $a_{i} = 2^{k_{i}}q_{i}$, where $k_{i} \geq 0$ is an integer, and $q_i$ is an odd integer.

$$\displaylines{f(i) = q_{i} \\
f : \{1, \dots, n+1\} \rightarrow \{1, 3, 5, \dots, 2n-1\}}$$

By the pigeonhole principle : $$\displaylines{f(i)=f(j),\; \text{for some }i \neq j}$$
$$a_{i} = 2^{k_{i}}q,\;a_{j} = 2^{k_{i}}q, \; \text{Assume without loss of generality that } k_{i}\geq k_{j}$$
Then, $$\displaylines{\frac{a_{i}}{a_{j}} = \frac{2^{k_{i}}q}{2^{k_{i}}q} = 2^{k_{i}-k_{j}} \; \text{is an integer because } k_{i} \geq k_{j}.}$$


---
##### The Erdös-Szekeres Theorem

Every sequence of $n^2 + 1$ distinct numbers contains an increasing subsequence of length $n+1$ or a decreasing subsequence of length $n+1$.

Proof :
Let $a_{1},\dots,a_{n^2+1}$ be a sequence of distinct numbers.
	For each $i \in \{1,\dots,n^2+1\}$, let $inc_{i} =$ the length of the longest increasing subsequence that starts with $a_{i}$.
	If $inc_{i} \geq n$ for some $i$, then we're done.
	Else $inc_i \in \{1, \dots,n \}$
	$\lceil \frac{n^2+1}{n} \rceil = n+1$

There exists $i_{1}, \dots, i_{n+1}$ such that $inc_{i_{1}} = inc_{i_{2}} = \dots = inc_{in+1}$ or $inc_{i_{1}} \rightarrow \dots \rightarrow inc_{in=1}$
∴ $a_{i_{1}} > a_{i_{2}} > \dots > a_{in+1}$


**Example :** 
Sequence : 10, 9, 5, 2, 1, 6, 3, 7, 4, 8

$$n^2 +1 \text{ where n=3, then }  3^2 + 1 = 10 \text{ distinct numbers.}$$
Increasing Subsequence : $1, 3, 4$
Decreasing Subsequence : $10, 9, 7$




