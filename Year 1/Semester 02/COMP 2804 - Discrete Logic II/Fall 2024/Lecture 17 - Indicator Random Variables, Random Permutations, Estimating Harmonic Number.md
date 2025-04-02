
#### Indication Random Variable

An **indicator random variable** is a type of random variable that takes on only two values, typically 0 and 1, to indicate whether a certain event occurs.

**Definition :** 
	A random variable $B : S \rightarrow \{0, 1\}$ is an indicator random variable.


**Properties :** 
1. **Expectation**: The expectation of an indicator random variable equals the probability of the event occurring : $$E(I_{A}) = 1 · P(A) + 0 · P(A^c) = P(A)$$

2. **Linearity of Expectation**: If $X$ is the sum of multiple indicator variables, we can compute its expectation as: $$E(X) = E(I_{A_{1}} + \dots + I_{A_{n}}) = P(A_{1}) + P(A_{n})$$

Example : 
n - people
d - days in a year
$X$ = "The number of pairs of people that have the same birthday"

For each $i, j \in \{1, \dots, n\}\; i \ne j$,  let $X_{i, j} = \left\{ \begin{array}{rcl} 1 & \text{ if person i and person j have the same birthday} \\ 0 & \text{ otherwise} \end{array} \right.$

By definition of expectation : $$E(I_{i, j}) = (1 \times P(I_{i, j} = 1)) + (0 \times P(I_{i,j} = 0))$$
since $P(I_{i,j} = 1) = \frac{1}{d}$ : $$E(I_{i,j}) = \left( 1 \times \frac{1}{d} \right) + \left( 0 \times \frac{1}{d} \right) = \frac{1}{d}$$
Giving us : $$E(X) = \sum_{1 \le i < j \le n} \frac{1}{d}$$
Since the probability is the same for every pair of people, we can just multiply by the number of combinations of birthday pairs that exist.

Number of combinations of two people : $$\binom{n}{2}$$
Therefore, our expected value is :
$$\displaylines{E(X) = \binom{n}{2} · \frac{1}{d} \approx 0.693}$$


---
#### Random Permutations

Example : Insertion Sort

```
InsertionSort(a, n) // sort a[0], ..., a[n-1]
	for i=1 to n-1
		j=1
		while j >= 1 and a[j-1] > a[j]
			swap a[j-1] <-> a[j]
			j <- j-1
```

If 'a' is random permutation from 1...n, then was is $E(X) =$ # of times the swap executes.

For each $1 \le x < y \le n$, define $$I_{x, y} = \left\{ \begin{array}{rcl}1 & \text{ if y appears before x in the input array 'a'} \\ 0 & \text{otherwise} \end{array} \right.$$
$$\displaylines{E(X) = E\left( \sum^{n-2}_{x=0}\sum^{n-1}_{y=x+1}I_{x, y} \right) = \sum^{n-2}_{x=0}\sum^{n-1}_{y=x+1}E(I_{x,y}) = \sum \sum \frac{1}{2} 
\\ = \binom{n}{2} \times \frac{1}{2}  = \frac{n(n-1)}{4}}$$


---
#### Estimating Harmonic Number
$$\displaylines{H_{n} = \sum^n_{i=1} \frac{1}{i} \\
\ln(n) \le H_{n} \le \ln(n) +1}$$

| Approximation | Formula          | Error    |
| ------------- | ---------------- | -------- |
| Basic         | ln(n)            | High     |
| Improved      | ln(n) + γ        | Low      |
| Even Better   | ln(n) + γ + 1/2n | Very Low |
|               |                  |          |


Example : 

```
findMax(a, n)
	max = -infinity
	for i=1 to n-1
		if a[i] > max :
			max = a[i] // *
```

X = The number of times the line * executes when 'a' is a random permutation of {1...n}.
$$\displaylines{X_{i} = \left\{\begin{array}{rcl}
1 & \text{if } a[i] = max\{a[1], \dots, a[i]\} \\
0 & \text{otherwise}
\end{array} \right. \\ \\
E(X_{i}) = \frac{1}{i} \\ 
E(X) = E\left( \sum^n_{i=1}X_{i} \right) = \sum^n_{i=1}E(X_{i}) = \sum^n_{i=1} \frac{1}{i} = H_{n}}$$



