**Content :**
	Exponents  
	Logarithms  
	Factorials and Binomials  
	Summations  
	Probability and Expected Value  
	Asymptotic Analysis



---
#### Exponents

$$2^5 = 2 · 2 ·2 ·2 ·2 $$
$$\displaylines{\text{Another way to write this is :} \\
2^5 = \prod^5_{i=1}2}$$

$$\displaylines{\text{In general :} \\
a^b = \prod^b_{i=1}a = \underbrace{2 ·2 ·2 \dots}_{\text{b times}}  }$$


---
#### Logarithms

$$\displaylines{\text{In some sense, the inverse of the exponent is the logarithm :} \\
\log_{2} 32 = \log_{2}2^5 = 5 \\ \\
\log_{2}32 \text{ is the answer to the question :} \\
2^? = 32 \\ \\
\text{Since its the inverse we can do :} \\
2^{\log_{2}32} = 32}$$


$$\displaylines{\text{We can change the base of a log :} \\
\log_{a}c = \frac{\log_{b}c}{\log_{b}a} \\ \\
\text{Example : }\\
\log_{2}32 = \frac{\log_{10}32}{\log_{10}2} \\
\log_{10}32 = \log_{2}32 · \log_{10}2}$$


---
#### Factorials

$$\displaylines{\text{In general :} \\ n! = 1 · 2 · 3 \dots (n-1) · n \\ \\ 5! = 1 · 2 · 3 · 4 · 5 = 120 \\ \\
\binom{n}{k} = \frac{n!}{k!(n-k)!}}$$


---
#### Summations

$$\displaylines{\sum^n_{i = 1} F() \\ \\
\text{We can split summations :} \\
\sum^n_{i=1}5 = \sum^n_{i=1} (2+3) = \sum^n_{i=1}2 + \sum^n_{i=1}3 \\ \\
\text{Common Closed Forms :} \\
\sum^n_{i=1}i = 1+2+3+\dots+(n-1)+n = \frac{n(n+1)}{2} \\ \\
\sum^n_{i=1} \frac{1}{i} = 1 + \frac{1}{2} + \dots + \frac{1}{n} = H_{n}}$$


---
#### Probability

$$\displaylines{\text{Flip a coin :} \\
S = \{H, T\} \\
P(H) = \frac{1}{2}, P(T) = \frac{1}{2} \\ \\
\text{Roll a die :} \\
S = \{1, 2, 3, 4, 5, 6\} \\
P(X=x) = \frac{1}{6}}$$


---
#### Expected Value

$$\displaylines{\text{We want to know the value, on average, over multiple experiements :} \\
E(X) = \sum^6_{i=1} i · P(X = i) = 1· \frac{1}{6} + 2 · \frac{1}{6} + \dots + 6 · \frac{1}{6} = \frac{1}{6}(1+2+3+4+5+6)\\
= \frac{7}{2} = 3.5 \\ \\
\text{If we want to know the outcome of two dice, we can use linearity of expectation :} \\
\text{Let B = "The value of the blue die"} \\
\text{Let R = "The value of the red die"} \\
\text{Let X = "The sum of the red and blue dice"} \\
X = B+R \\ \\
\text{The expected value of X is :} \\
E(X) = E(B) + E(R) \\
= \frac{7}{2} + \frac{7}{2} = 7}$$


---
#### Indicator Random Variables

$$\displaylines{\text{Flip a fair coin n times.} \\
\text{Let X = "The number of times the coin comes up HEADS"}\\ \\
\begin{cases}
{ X_{i} = 1  \text{ if coin i comes up HEADS}} \\
{X_{i} = 0 \text{ otherwise (TAILS)}}
\end{cases} \\ \\
\text{The expected value of } X_{i} : \\
E(X_{i}) = 0 · P(X = 0) + 1 · P(X = 1) \\
= P(X = 1) \\
= P(\text{Coin i is HEADS}) \\ = \frac{1}{2} \\ \\
E(X) = E(X_{1} + X_{2} +X_{3} + \dots + X_{n}) \\
=E(X_{1}) + E(X_{2}) + E(X_{3}) + \dots + E(X_{n}) \\
\underbrace{\frac{1}{2} + \frac{1}{2} + \dots + \frac{1}{2}}_{\text{n times}} = \frac{n}{2}}$$


---
#### Asymptotic Analysis


Insertion Sort

```
InsertionSort(array, n):  
	for (i = 0; i < n -1; i++):  
		s = i // s for smallest  
		for (j = i + 1; j < n; j++):  
			if (array[j] < array[s]):  
				s = j  
	swap(array , i, s)  
	
swap(array, i, s):  
	temp = array[i]  
	array[i] = array[s]  
	array[s] = temp
```

**swap** in outer loop (4 accesses).  
**comparison** in inner loop (2 accesses). $$\displaylines{\text{Outer Loop :} \sum^{n-2}_{i = 0} \\
\text{Inner Loop : } \sum^{n-1}_{j = i+1} \\ \\
\sum^{n-2}_{i=0}\left( 4 + \sum^{n-1}_{j=i+1}2 \right) 
= \sum^{n-2}_{i=0}\left( 4 + \sum^{n-1}_{j=1}2 \right) 
= \sum^{n-2}_{i=0}(4 + 2 · (n - i - 1)) \\ \\
2· \sum^{n-2}_{i=0}2 + n - i - 1 =
2 · \sum^{n-2}_{i=0}n - i +1 = 2 · \left( \sum^{n-2}_{i=0}n - \sum^{n-2}_{i=0}i - \sum^{n-2}_{i=0}1 \right) \\ \\
2 ·(n(n-1) - \frac{n(n-1)}{2} + (n-1)) \\
= n(n-1) + 2(n-1) \\
= n^2 -n +2n - 2 \\
= n^2 + n -2 \\ \\
\text{On a call to InsertionSort(array, n),there are n2 + n − 2 memory accesses.}}$$
On a call to InsertionSort(array, n), there are 3n2 − 2n − 1 memory accesses.  
$$\displaylines{\text{Let } IS(n) = n^2 + n − 2. \\
\text{Then } IS(n) = O(n^2)  \\
\text{if there exists constants c and k such that }IS(n) ≤ c · n^2, for\; all\; n ≥ k. \\ \\
n^2 + n − 2 ≤ n^2 + n \;for\; n ≥ 1  \\
≤ n^2 + n^2 \;for\; n ≥ 1  \\
≤ 2n^2 \;for\; n ≥ 1  \\ \\
Thus\; IS(n) = O(n^2) \;with\; c = 2\;  k = 1\\ \; and\;InsertionSort(array, n)=O(n^2)\; with\; c = 2\; and\; k = 1}$$







