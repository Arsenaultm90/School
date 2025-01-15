##### Recall

**Theorem :**
	Let $S$ be an $n$-element set. There are $n!$ permutations of $S$.

**Proof :**
	Use product rule or observe that a permutation is one-to-one function $f : \{1, \dots, n\} \rightarrow S$


---
##### Binomial Coefficients
	$$\displaylines{\text{Let } n \geq 0,\; k \geq 0 \text{ be integers}. \\
	\text{Then } \binom{n}{k} \text{ is the number of } 'k'\text{-element subsets of a set of size } 'n'.}$$

**Theorem :**
$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

**Proof :** (Combinatorial proof/Counting two ways)

Let S be a set of size $n$.
Let A be the ordered k-element subsets of S.

i) Product Rule :
1. Choose a k-element subset of S. $\binom{n}{k}$
2. Choose an order for this subset. $k!$
$$\binom{n}{k} \times k! = |A|$$

ii) Product Rule : 
	For i = 1 to k, choose the $i^{th}$ element in the ordered set.
$$|A| = n \times (n-1) \times \dots \times (n-(k-1) \times (\frac{(n-k)\times(n-k-1)\times\dots \times 1}{(n-k)\times(n-k-1)\times\dots \times 1})$$
$$|A| = \frac{n!}{(n-k)!}$$

Simplifying :
$$\displaylines{\frac{1}{k!} \times \binom{n}{k} \times k! = \frac{1}{k!} \times \frac{n!}{(n-k)!}\\ \\
\binom{n}{k} = \frac{n!}{k!(n-k)!}}$$

**Example :**
How many 5-card hands of a 52-card deck are there?

$$\binom{52}{5} = \frac{52 \times 51 \times 50 \times 49 \times 48}{5 \times 4 \times 3 \times 2 \times 1} = 2, 598, 960$$

**Example :** 
How many bitstrings of length $n$ have exactly $k$ 1's?

$$\binom{n}{k}$$


---
##### Newton's Binomial Theorem

For integer $n \geq 0$,
$$(x + y)^n = \sum^{n}_{k=0}\binom{n}{k}·x^{n-k}·y^k$$

**Example :** 
What is the coefficient of $x^{12}y^{13}$ in $(2x - 5y)^{25}$?

For the expression $(2x−5y)^{25}$, you want to find the term that contains $x^{12}y^{13}$. 
The key is to match the exponents of x and y in the general term: 
	The exponent of x is n−k, which should be 12. 
	The exponent of y is k, which should be 13. 
	
Setting the exponents equal to the desired powers: 
	$n−k=12$ 
	$k=13$ 
	
Since $n=25$, we have: 
	$25 - k = 12$ 
	$k = 13$

$$\displaylines{\binom{25}{13}(2x)^{12}(-5y)^{13} \\
- \binom{25}{13}·2^{12}·5^{13}·x^{12}y^{13} \\
∴ \text{Binomial Coefficient of } x^{12}y^{13} \text{ is } \binom{25}{13}·2^{12}·5^{13}}$$


Theorem : 
$$\sum^{n}_{k=0}\binom{n}{k} = 2^n$$


---

