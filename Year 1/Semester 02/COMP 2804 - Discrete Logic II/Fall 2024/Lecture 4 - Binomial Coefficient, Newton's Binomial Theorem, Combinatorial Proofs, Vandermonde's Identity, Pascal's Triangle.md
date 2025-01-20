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
$$(x + y)^n = \sum^{n}_{k=0}\binom{n}{k}·x^{k}·y^{n-k}$$

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
### Combinatorial Proofs

##### Symmetry Property of Binomial Coefficients

**Theorem : $$\displaylines{\binom{n}{k} = \binom{n}{n-k}}$$**
**Proof : $$\displaylines{\text{Let S be a set of size 'n'. Let A be the set of k-element subsets of S.}\\
\binom{n}{k} = |A| = \binom{n}{n-k} \\ \\
\text{Use Product Rule}:\\
\text{Choose n-k elements in S and remove them.}\\
\text{Return the remaining k-elements of S.}}$$
---
##### Pascal's Identity

A mathematical theorem that describes the relationship between **Binomial coefficients** and **Pascal's Triangle**.

**Theorem :** $$\displaylines{
\binom{n+1}{k} = \binom{n}{k} + \binom{n}{k-1}}$$
**Proof :**  $$\displaylines{\text{Let S be a (n+1)-element set. Let A be the set of k-element subsets of S.}\\
\binom{n+1}{k} = |A| = \binom{n}{k} + \binom{n}{k-1} \\ \\
\text{Let } A_{1} \text{ be the sets in A that include 'x'.}\\
\text{Let } A_{2} \text{ be the sets in A that don't include 'x'.} \\ \\
|A| = |A_{1}| + |A_{2}|}$$


---
##### Vandermonde's Identity
Vandermonde's identity states that the sum of products of two binomial coefficients, where one selects $k$ items from a set of $n$ items and the other selects $r-k$ items from a set of $m$ items, is equal to the binomial coefficient that counts the number of ways to choose $r$ items from a combined set of $n+m$ items.

Theorem :  $$\displaylines{\binom{m+n}{r} = \sum^{r}_{k=0}\binom{m}{k}\binom{n}{r-k}}$$

Proof : $$\displaylines{\text{Let S be a set of size m+n.}\\
\text{Let A be the set of r-element subsets of S.}\\
\binom{m+n}{r} = |A| = \sum^{r}_{k=0}\binom{m}{k} \binom{n}{r-k} \\ \\
\text{For each } k \in \{0, \dots, r\}, \text{ let } A_{k} \text{ be all the subsets in A that include exactly 'k' elements from } S_{1} \\ (\text{So they contain exactly r-k elements from } S_{2})}$$
$$\displaylines{|A| = |A_{0}| + |A_{1}| + |A_{2}| + \dots + |A_{r}| = \sum^{r}_{k=0}|A_{k}| \\ \\
\text{Product Rule} \\
\text{Choose k elements from } S_{1}\\
\text{Choose } r-k \text{ elements from } S_{2}\\
\binom{m}{k} ·\binom{n}{r-k} \\ \\
|A| = \sum^{r}_{k=0}\binom{m}{k} ·\binom{n}{r-k}}$$

Example :
Let $n = 3,\; m = 2, \; r=3$
$$\sum^{3}_{k=0}\binom{3}{k}\binom{2}{3-k} = \binom{3+2}{3}$$
$$\displaylines{\text{Sum of Products of Binomial Coefficients :}\\
\binom{3}{0}\binom{2}{3}+\binom{3}{1}\binom{2}{2}+\binom{3}{2}\binom{2}{1}+\binom{3}{3}\binom{2}{0}\\ \\
\binom{3}{0}\binom{2}{3} = 1 \times 0 = 0\\
\binom{3}{1}\binom{2}{2} = 3 \times 1 = 3 \\
\binom{3}{2}\binom{2}{1} = 3 \times 2 = 6 \\
\binom{3}{3}\binom{2}{0} = 1 \times 1 = 1 \\ \\
0+3+6+1 = 10}$$
$$\displaylines{\text{Single Binomial Coefficient :}\\ \binom{3+2}{3} = \binom{5}{2} = 10}$$