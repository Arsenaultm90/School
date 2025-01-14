##### Bijection Rule
$$\displaylines{\text{If there exists a bijection } f:A\rightarrow B,\; \text{then } |A| = |B|. }$$

##### Product Rule
$$\displaylines{A = \text{The set of possible executions of procedure P.} \\
B = S = \text{The set we want to know the size of.}}$$


**Example:**
$$\displaylines{X = \text{A n-elements set}\\
X = \{a, b, c\}\\ \\
\text{Power Set}\\
P(X) = \text{The set of all subsets of 'X'}\\
P(X) = \{\varnothing, \{c\}, \{b\}, \{b,c\}, \{a\}, \{a, c\}, \{a, b\}, \{a, b, c\} \}}$$
$$\displaylines{\text{Let } X= \{x_{1}, x_{2}, x_{3},\dots,x_{n}\}\\
\text{For any subset } S \subseteq X,\; \text{define } f(s)  = b_{1}\;b_{2}\;b_{3}\;\dots\; b_{n} \\
\text{where } b_{i} = \left\{ \begin{array}{c} 0,\; \text{if } x_{i} \not\in S \\ 1, \; \text{if } x_{i} \not\in S \end{array} \right. \\ \\
f(\varnothing) = 000 \\
f(c) = 001 \\
f(b) = 010 \\
f(b, c) = 011 \\
f(a) = 100 \\
f(a, c) = 101 \\
f(a, b) = 110 \\
f(a, b, c) = 111 \\ \\
 f \text{ is a bijection from P(X), or set A, to binary strings of length } n. \\
 ∴ |P(X)| = |S_{n}| = 2^n}$$

---

##### Complement Rule
$$\displaylines{\text{If } A \subseteq U, \text{ then } |A| = |U| -|U \setminus A|.}$$

**Example:**
A password is a string of eight characters over the alphanumeric set, $\sum =\{a, b, c, \dots, z, 0, 1, 2,\dots,9\}$, that contains at least one digit.

Let 'S' be the set of possible passwords.
Let 'U'  = all 8-character strings over $\sum$.

$$\displaylines{|\sum| = 36^8 \\ \\
U\setminus S = \text{"Strings over U with no digits"} -\{a, b, c, \dots, z\}\\
|U\setminus S| = 26^8\\ \\
|S| = |U| - |U\setminus S| = 36^8 - 26^8 = 2,612, 282, 842, 880}$$

---
##### The Sum Rule
$$\displaylines{\text{If A and B are disjoint, then } |A\cup B| = |A| +|B|.}$$
Disjoint : $A \cap B = \varnothing$

**Example:**
