$$\displaylines{f : \mathbb{N} \rightarrow \mathbb{N} \\ \\
f(n) = \begin{cases}
3 & \text{if n = 0} \\
2f(n-1)+3 & \text{if }\geq 1
\end{cases}}$$
$$\displaylines{f(1) = 2f(1-1)+3 = 9 \\
f(2) = 2f(2-1) +3= 21 \\
f(3) = 2f(3-1)+3= 45 \\
f(4) = 2f(4-1)+3 = 93}$$

**Claim :** $f(n) = 3\times2^{n+1}-3$

**Proof By Induction on $n$ :** 
$$\displaylines{\text{Base Case : }n = 0 \\
3\times {2^{0+1}-3} = 3 \\ \\
\text{Inductive Step : Assume }f(k) = 3\times 2^{k+1} - 3 \text{ for all } k \in \{0, 1, 2, \dots, n-1\} \\ \\
\text{Prove for } f(n) : \\
f(n) = 2· f(n-1) +3 \\
2·(3·2^{n}-3)+3 \\
3·2^{n+1} -6 + 3 \\ \\
\text{QED } \\ 3·2^{n+1}-3}$$


**Example :** 
$$\displaylines{\text{n Factorial} \\n! \\f(n) = \begin{cases}
1 & \text{if } n=0\\
n·f(n-1) & \text{if } n\geq
 1\end{cases} \\ \\ \\ \\
 \text{Pascal's Identity} \\
 B(n, k) = \binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k} \\ \\
 B(n, k) = \begin{cases}
1 & \text{if } k = 0 \text{ and } n =0 \\
1 & \text{if } n = k \geq 0 \\
B(n-1, k-1)+B(n-1, k) & \text{if }n \geq 1 \text{ and } 1 \leq k \leq n-1
\end{cases}}$$



##### Fibonacci Function
$$\displaylines{f(n) = \begin{cases}
0 & \text{if } n = 0 \\
1 & \text{if } n = 1 \\
f(n-1)+f(n-2) & \text{if } n \geq 2
\end{cases}}$$

**Claim :** $$\displaylines{f(n) = \frac{\varphi^n-\psi^n}{\sqrt{ 5 }} \text{ where,} \\
\varphi = \frac{1+\sqrt{ 5 }}{2}, \; \psi = \frac{1-\sqrt{ 5 }}{2} \\
\phi\;\text{and}\;\psi \text{ are the solutions to }x^2 = x+1}$$

**Proof By Induction :** $$\displaylines{\text{Base Case : }n=0 \\
\frac{\varphi^0-\psi^0}{\sqrt{ 5 }} = \frac{1-1}{\sqrt{ 5 }} = 0 \\ \\ \\
\text{Base Case : }n=1 \\
\frac{\varphi^1-\psi^1}{\sqrt{ 5 }} = \frac{\frac{1+\sqrt{ 5 }}{2} - \frac{1-\sqrt{ 5 }}{2}}{\sqrt{ 5 }} = \frac{\sqrt{ 5 }}{\sqrt{ 5 }} = 1 \\ \\ \\
\text{Inductive Step : } \\ f(k) = \frac{\varphi^k-\psi^k}{\sqrt{ 5 }} \text{ for all } k \in \{0, 1, 2, \dots, n-1\} \\
f(n) = f(n-1) + f(n-2) \\ \\
\frac{\varphi^{n-1}-\psi^{n-1}}{\sqrt{ 5 }} + \frac{\varphi^{n-2}-\psi^{n-2}}{\sqrt{ 5 }} \\
\frac{\varphi^{n-1} + \varphi^{n-2}- (\psi^{n-1}+\psi^{n-2})}{\sqrt{ 5 }} \\
\frac{\varphi^{n-2}(\varphi+1) - \psi^{n-2}(\psi+1)}{\sqrt{ 5 }} \\ \\
\text{Remember : } \phi \text{ and } \psi \text{ are solutions to } x^2 = x +1 \\
\varphi^2 = \varphi +1, \; \psi^2 = \psi +1\\ \\
∴ \frac{\varphi^n - \psi^n}{\sqrt{ 5 }}}$$


**Example :** 
00 - Free Bitstrings
Let $S$ be the set of of $n$-bit binary strings that do not contain two consecutive 0's.
$$\displaylines{S_{0} = \{\varepsilon\} \\
S_{1} = \{0, 1\} \\
S_{2} = \{01, 10, 11\} \\
S_{3} = \{010, 011, 101, 110, 111\}}$$

How big is $S_{n}$?
A string in $S_{n}$ is either :
	Starts with a 1 followed by any string in $S_{n-1}$
	OR
	Starts with 01 followed by any string in $S_{n-2}$

$$\displaylines{S_{n} = A \cup B \\
|S_{n}| = |A| + |B| = |S_{n-1} | + |S_{n-2}|\\ \\ 
|S_{n}|
\begin{cases}
1 & \text{if } n=0 \\
2 & \text{if } n = 1 \\
|S_{n-1}| + |S_{n-2}| & \text{if } n\geq 2
\end{cases}
}$$



**Example :**
$aa$-free strings over $\{a, b, c\}$
Let $S$ be the set of of $n$-bit binary strings that do not contain two consecutive $a$'s.
$$\displaylines{S_{0} = \{\varepsilon\} \\
S_{1} = \{a, b, c\} \\
S_{2} = \{ab, ac, ba, bb, bc, ca, cb, cc\}}$$

A string in $S_{n}$ is either : 
	Starts with $b$ followed by any string in $S_{n-1}$
	Starts with $c$ followed by any string in $S_{n-1}$
	Starts with $ab$ followed by any string in $S_{n-2}$
	Starts with $ac$ followed by any string in $S_{n-2}$

$$\displaylines{|S_{n}| =\begin{cases}
1 & n = 0 \\
3 & n =1 \\
2|S_{n-1}|+2|S_{n-2}| & n \geq 2
\end{cases}}$$


**Claim : $$\displaylines{\frac{(3-2\sqrt{ 3 })(1-\sqrt{ 3 })+(3+2\sqrt{ 3 })(1+\sqrt{ 3 })}{6}}$$**



**Example :** 
$ab$-free strings over $\{a, b, c\}$
Let $S$ be the set of of $n$-bit binary strings that do not contain $ab$.
$$\displaylines{S_{0} = \{\varepsilon\} \\
S_{1} = \{a, b, c\} \\
S_{2} = \{aa, ac, ba, bb, bc, ca, cb, cc\}}$$

A string in $S_{n}$ is either : 
	Starts with $b$ followed by any string in $S_{n-1}$
	Starts with $c$ followed by any string in $S_{n-1}$
	Starts with $ac$ followed by any string in $S_{n-2}$
	Starts with $aac$ followed by any string in $S_{n-3}$
	Starts with ...

$$\displaylines{|S_{n}| = 2|S_{n-1}| + \sum^{n-2}_{k=0}|S_{k}|}$$



