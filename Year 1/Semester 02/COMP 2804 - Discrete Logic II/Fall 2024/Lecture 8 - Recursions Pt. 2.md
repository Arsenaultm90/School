
**Fibonacci Example :** 
How many ways are there to write $n$ as a sum of twos and ones?$$\displaylines{f(1) = 1\\
f(2) = \begin{cases}
1+1 = 2 \\
2 = 2
\end{cases} \\
f(3) = \begin{cases}
1 + 1 + 1 = 3 \\
1 + 2 = 3 \\
2 + 1 = 2
\end{cases}}$$

$F_{n}$ = # of ways to write $n$ as the sum of twos and ones.

For $n \geq 2$, we can either :
	Start with a 1 followed by any sum of ones and twos that add up to $n$. ($F_{n-1}$)
		$1 + f(n-1) = n$
	Start with a 2 followed by any sum of ones and twos that add up to $n$. ($F_{n-2}$)
		2 + $f(n-2) = 2$

$F_{n} = F_{n-1} + F_{n-2}$
∴ $F_{n} = f_{n+1}(Fibonacci)$



---
##### Greatest Common Divisor - Euclid's Algorithm

Find the g.c.d of two integers where, $a > b \geq 1$.
	The largest integer $d$ that divides $a$ and $b$.
	If $a \text{ mod } b = 0$, then $gcd(a, b) = b$
		$a=q·b + 0$

Uses the $mod$ operator ( remainder after integer division)

For any positive integer $a$ and $b$.
	$a = q·b + r$, where $q$ is an integer and $r \in \{0, \dots, b-1\}$
	$a \text{ mod } b = r$

Example : $$\displaylines{a = 20 \\ b=6\\
a = 3·b+2}$$
**Lemma :**
	If $a \text{ mod } b = r \neq 0$ then,
		$gcd(a,b) = gcd(b, r)$ 

**Proof :** 
	Let $d$ be any common divisor of $a$ and $b$.
	$a = q·b + r$


```
Euclids(a,b) {           //Requires a > b >= 1
	r = a mod b
	if r=0 return b
	return gcd(b, r)
}
```


Example :$$\displaylines{gcd(34, 21),\; 34 = 1·21 + 13 \\
gcd(21, 13),\; 21 = 1·13 + 8 \\
gcd(13, 8),\;13 = 1·8 + 5 \\
gcd(8, 5),\; 8 = 1·5 + 3 \\
gcd(5, 3),\; 5=1·3 + 2 \\
gcd(3,2),\; 3 = 1·2+1 \\
gcd(2,1)= 1}$$


Let $M(u,b)$ = The number of mod operations performed by Euclids(a,b).

**Claim :** 
	Let $a>b \geq 1$ and let $m = M(a,b)$
		Then, $a \geq f_{m+2}$ and $b \geq f_{m+1}$


**Proof By Induction :** 
	Base Case : $m = 1$ $$\displaylines{a > b \geq 1,\; \; a\geq 2 \\
	b \geq f_{1+1} = f_{2} = 1 \\
	a \geq f_{1+2} = f_{3} = 2}$$
	