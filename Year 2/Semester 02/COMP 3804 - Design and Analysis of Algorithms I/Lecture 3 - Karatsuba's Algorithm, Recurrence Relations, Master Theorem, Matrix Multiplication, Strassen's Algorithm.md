## Master Theorem

$a \geq 1, b \geq 2, d \geq 0$

$T(n) \le \begin{cases} 1 & \text{ if n = 1} \\ n^d + a * T\left( \frac{n}{b} \right) &\text{ if n} \ge 2 \end{cases}$

**Conditions :**
$d > \log_{b}a : T(n) = O(n^d)$
$d = \log_{b}a : T(n) = O(n^d \log n)$
$d < \log_{b}a : T(n) = O(n^{\log_{b}a})$


Example:
Input : $nxn$ matrices X, Y
Output: $n x n$ matrix Z = XY

$Z_{ij} =$ Dot product of row $i$ in X and column $j$ in Y.
Compute $Z_{ij}$ in O(n) time.
Number of entries is $n^2$
Total time O$(n^3)$


**Master Theorem :**
$X = \begin{bmatrix}   A & B\\   C & D  \end{bmatrix} ·\ Y= \begin{bmatrix}   E & F\\   G & H  \end{bmatrix}$

$= \begin{bmatrix}   AE + BG & AF + BH\\   CE + DG & CF+DH  \end{bmatrix}$

To Compute XY :
	Eight recursive calls on $\frac{n}{2} · \frac{n}{2}$ matrices
	Four additions of $\frac{n}{2} · \frac{n}{2}$ matrices

$T(n) = n^2 + 8·T\left( \frac{n}{2} \right)$

$d = 2, a = 8, b = 2$
$T(n) = O(n^3)$



---
## Strassen's Algorithm

You can reduce the **number of recursive multiplications** from 8 to 7.

$P_{1} = A(F-H)$
$P_{2} = (A+B)H$
$P_{3} = (C+D)E$
$P_{4} = D(G-E)$
$P_{5} = (A+D)(E+H)$
$P_{6} = (B-D)(G+H)$
$P_{7} = (A-C)(E+F)$

$XY = \begin{bmatrix}   P_{5} + P_{4} - P_{2} + P_{6} & P_{1} + P_{2}\\   P_{3} + P_{4} & P_{1} + P_{5} - P_{3} - P_{7}  \end{bmatrix}$

$O(n^{\log{7}})$
