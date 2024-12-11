##### Orthogonal Complements

Two vectors are **orthogonal** to each other if their dot product equals 0.
$\vec x · \vec y = 0$

$X = \{\vec x_{1},\; \vec x_{2},\; \dots,\; \vec x_{n}\}$
$X^\perp = \{\vec y_{1},\; \vec y_{2},\; \dots,\; \vec y_{m}\}$
If the dot product of every vector in a set, with every other vector in another set, results in 0, then we can say that that set is the **Perpendicular** set.

Ex.
$$\displaylines{V = span(\left[\begin{array}{c}1 \\ 0 \\ 2 \end{array}\right],\; \left[\begin{array}{c}-1 \\ 1 \\ 3 \end{array}\right]) \\
V^\perp = \{\vec{x} \in {\rm I\!R}^3 |\; \vec{x}·\left[\begin{array}{c}1 \\ 0 \\ 2 \end{array}\right] = 0\; AND\; \vec{x}·\left[\begin{array}{c}-1 \\ 1 \\ 3 \end{array}\right]=0\}}$$
$$\displaylines{\vec{x} = (x_{1}, x_{2}, x_{3}) \\
1x_{1} + 0x_{2} + 2x_{3} = 0 \\
-1x_1 + 1x_{2} + 3x_{3}= 0 \\ \\ Augmented\; Matrix: \\
\left[\begin{array}{ccc|r}1 & 0 & 2 & 0 \\ -1 & 1 & 3 & 0 \end{array}\right] \Rightarrow \left[\begin{array}{ccc|r}1 & 0 & 2 & 0 \\ 0 & 1 & 5 & 0 \end{array}\right] \\ \\
x_{1}+ 2x_{3} = 0 \Longrightarrow x_{1} = -2x_{3} \\ x_{2} + 5x_{3} = 0 \Longrightarrow x_{2} = -5x_{3} \\
\left[\begin{array}{c}x_{1} \\ x_{2} \\ x_{3} \end{array}\right] = \left[\begin{array}{c}-2 \\ -5 \\ 1 \end{array}\right] \\
∴ V^\perp = span\left(\left[\begin{array}{c}-2 \\ -5 \\ 1 \end{array}\right]\right)}$$
	The vector we find that spans the perpendicular subspace $V^\perp$ in $\mathbb{R}^3$ corresponds to a line that is orthogonal to the plane $V$ in $\mathbb{R}^3$. 


---

##### Orthogonal Complements of The Fundamental Subspaces

The **Row Space** and the **Null Space** are orthogonal to each other. 
$c(A^T) · N(A) = 0$

The **Column Space** and the **Left Null Space** are orthogonal to each other.
$c(A)·N(A^T)=0$

$\mathbb{R}^n : V, V^\perp$ 
$n = Dim(V)+Dim(V^\perp)$

$Dim(c(A^T)) = r(rank\; of\; A)$
$Dim(N(A)) = n - r$
$Dim(c(A)) = r$
$Dim(N(A^T)) = m - r$

Ex.
$$\displaylines{A=\left[\begin{array}{cccc}1 & 0 & 0 & 2 \\ -1 & 1 & 2 & 0 \\ 2 & 0 & -1 & 1 \end{array}\right]\begin{aligned}\;RREF \\ ==\Longrightarrow \end{aligned} \left[\begin{array}{cccc}1 & 0 & 0 & 2 \\ 0 & 1 & 0 & -4 \\ 0 & 0 & 1 & 3 \end{array}\right]}$$

| Space    | Realm                           | Dimension          |
| -------- | ------------------------------- | ------------------ |
| $c(A)$   | <center>$\mathbb{R}^3$</center> | <center>3</center> |
| $N(A)$   | <center>$\mathbb{R}^4$</center> | <center>1</center> |
| $c(A^T)$ | <center>$\mathbb{R}^4$</center> | <center>3</center> |
| $N(A^T)$ | <center>$\mathbb{R}^3$</center> | <center>0</center> |
$c(A) =span(\left[\begin{array}{c}. \\ . \\ . \end{array}\right],\left[\begin{array}{c}. \\ . \\ . \end{array}\right],\left[\begin{array}{c}. \\ . \\ . \end{array}\right])$

$N(A) = span(\left[\begin{array}{c}. \\ . \\ . \\ . \end{array}\right])$

$c(A^T) = span(\left[\begin{array}{c}. \\ . \\ . \\ . \end{array}\right],\left[\begin{array}{c}. \\ . \\ . \\ . \end{array}\right],\left[\begin{array}{c}. \\ . \\ . \\ . \end{array}\right])$

$N(A^T) = \left[\begin{array}{c}0 \\ 0 \\ 0 \end{array}\right]$


---
##### Projection Onto The Subspace
![[Screenshot 2024-12-04 at 8.02.00 AM.png]]
We can say that:
$\vec v \in L$
$\vec w \in L^\perp$


Formula:$$\displaylines{Subspace\; V\; in\; \mathbb{R}^n  \\Proj_{v}A = A(A^TA)^{-1}A^T\vec{x}\\ Proj_{v}\vec{x} = \frac{v·u_{1}}{u_{1}·u_{1}}u_{1} + \dots + \frac{v·u_{n}}{u_{n}·u_{n}}u_{n}}$$
Ex:$$\displaylines{V = span(\left[\begin{array}{c} 2 \\ 1\\ 1\end{array}\right],
\left[\begin{array}{c}1 \\ 0\\ -1\end{array}\right])\\ \\
Step \; 1\; Find\; A\; and\; A^T:\\
A = \left[\begin{array}{cc} 2 & 1\\ 1 & 0\\ 1 & -1\end{array}\right], 
\;A^T = \left[\begin{array}{cc} 2 & 1 & 1\\ 1 & 0 & -1\end{array}\right]\\ \\
Step \; 2\; Evaluate\; A^T\; A:\\
A^TA = \left[\begin{array}{cc} 2 & 1 & 1\\ 1 & 0 & -1\end{array}\right]\left[\begin{array}{cc} 2 & 1\\ 1 & 0\\ 1 & -1\end{array}\right] \\
= \left[\begin{array}{cc} 4+1+1 & 2+0-1\\ 2+0-1 & 1+0+1\end{array}\right]\\
= \left[\begin{array}{cc} 6 & 1\\ 1 & 2\end{array}\right]\\ \\
Step\; 3:\; Find\; The\; Inverse\\
\left[\begin{array}{cc|rr} 6 & 1 & 1 & 0\\ 1 & 2 & 0 & 1\end{array}\right] R_{1}\leftrightarrow R_{2}\\
\left[\begin{array}{cc|rr} 1 & 2 & 0 & 1\\ 6 & 1 & 1 & 0\end{array}\right] R_{2}-6R_{1}\\
\left[\begin{array}{cc|rr} 1 & 2 & 0 & 1\\ 0 & -11 & 1 & -6\end{array}\right](-\frac{1}{11})R_{2}\\
\left[\begin{array}{cc|rr} 1 & 2 & 0 & 1\\ 0 & 1 & -\frac{1}{11} & \frac{6}{11}\end{array}\right] R_{1}-2R_{2}\\
\left[\begin{array}{cc|rr} 1 & 0 & \frac{2}{11} & -\frac{1}{11}\\ 0 & 1 & -\frac{1}{11} & \frac{6}{11}\end{array}\right]\\ \\
Step\; 4:\; Simplify\\
\left[\begin{array}{cc} 2 & 1\\ 1 & 0\\ 1 & -1\end{array}\right]
\left[\begin{array}{cc} \frac{2}{11} & -\frac{1}{11}\\-\frac{1}{11} & \frac{6}{11}\end{array}\right]
\left[\begin{array}{cc} 2 & 1 & 1\\ 1 & 0 & -1\end{array}\right]\\
\left[\begin{array}{cc} \frac{4}{11}-\frac{1}{11} & -\frac{2}{11}+\frac{6}{11}\\ \frac{2}{11} + 0 & -\frac{1}{11} + 0\\ \frac{2}{11}+\frac{1}{11} & -\frac{1}{11}-\frac{6}{11}\end{array}\right]\left[\begin{array}{cc} 2 & 1 & 1\\ 1 & 0 & -1\end{array}\right]\\
\left[\begin{array}{cc} \frac{3}{11} & \frac{4}{11}\\ \frac{2}{11} & -\frac{1}{11} \\ \frac{3}{11} & -\frac{7}{11}\end{array}\right]\left[\begin{array}{cc} 2 & 1 & 1\\ 1 & 0 & -1\end{array}\right]\\
\left[\begin{array}{ccc} \frac{6}{11}+\frac{4}{11} & \frac{3}{11} + 0 & \frac{3}{11}-\frac{4}{11} \\ \frac{4}{11}-\frac{1}{11} & \frac{2}{11}-0 & \frac{2}{11}+\frac{1}{11} \\ \frac{6}{11}-\frac{7}{11} & \frac{3}{11}-0 & \frac{3}{11}+\frac{7}{11}\end{array}\right]\\
\left[\begin{array}{ccc} \frac{10}{11} & \frac{3}{11} & -\frac{1}{11} \\ \frac{3}{11} & \frac{2}{11} & \frac{3}{11} \\ \frac{-1}{11} & \frac{3}{11} & \frac{10}{11}\end{array}\right]\vec{x}\\
\frac{1}{11}\left[\begin{array}{ccc} 10 & 3 & -1 \\ 3 & 2 & 3 \\ -1 & 3 & 10\end{array}\right]\vec{x}}$$
What we find is a projection matrix where, for any $\vec x$, we can find the projection $\vec x$ that we choose to project onto $V$.


---
##### Least Squares Solution
The **least squares solution** in linear algebra is a method for finding an approximate solution to a system of linear equations that has no exact solution.

Instead of solving $A\vec x = b$ directly, we solve the problem: $$\displaylines{A^TA\vec{x}^* = A^T\vec{b}\\ or \\min_{x}||A\vec{x}-b||^2}$$
Ex.
$$\displaylines{-2x + y = 1\; \Longrightarrow\; y = 2x+1\\
-x + y = 0\; \Longrightarrow\; y = x\\
x + 2y = 3\; \Longrightarrow\; y = -\frac{1}{2}x + \frac{3}{2}\\ \\
There\; is\; no\; solution\;vector,\\
\left[\begin{array}{cc}
-2 & 1 \\ -1 & 1 \\ 1 & 2 
\end{array}\right]
\left[\begin{array}{cc}
x\\y
\end{array}\right] = 
\left[\begin{array}{cc}
1 \\ 0 \\ 3
\end{array}\right]\\ \\
So, we \; apply\; the\; fomula:\\
A^T = \left[\begin{array}{ccc}
-2 & -1 & 1\\1 & 1 & 2
\end{array}\right]\\
A^TA = \left[\begin{array}{ccc}
-2 & -1 & 1\\1 & 1 & 2
\end{array}\right]\left[\begin{array}{cc}
-2 & 1 \\ -1 & 1 \\ 1 & 2 
\end{array}\right]\\
= \left[\begin{array}{cc}
4+1+1 & -2-1+2 \\ -2 + -1 + 2 & 1 + 1 + 4 
\end{array}\right]\\
=\left[\begin{array}{cc}
6 & -1 \\ -1 & 6
\end{array}\right]\\
A^T\vec{b}= \left[\begin{array}{ccc}
-2 & -1 & 1\\1 & 1 & 2
\end{array}\right]\left[\begin{array}{cc}
1 \\ 0 \\ 3
\end{array}\right]\\
=\left[\begin{array}{cc}
-2+0+3 \\ 1+0+6
\end{array}\right]\\
=\left[\begin{array}{cc}
1 \\ 7
\end{array}\right]\\ \\
Now\; we\; have:\\
\left[\begin{array}{cc}
6 & -1 \\ -1 & 6
\end{array}\right]
\vec{x}^* = 
\left[\begin{array}{cc}
1 \\ 7
\end{array}\right]\\ \\
Augmented Matrix:\\
\left[\begin{array}{cc|r}
6 & -1 & 1\\ -1 & 6 & 7
\end{array}\right]\begin{aligned}\;RREF \\ ==\Longrightarrow \end{aligned}
\left[\begin{array}{cc|r}
1 & 0 & \frac{13}{35}\\ 0 & 1 & \frac{43}{35}
\end{array}\right]\\ \\
∴\vec{x}^* = \left[\begin{array}{cc}
\frac{13}{35} \\ \frac{43}{35}
\end{array}\right]}$$
Which is the vector that will most closely approximate the intersection point of lines.


---
##### Coordinates In A New Basis
Basis : $\beta = \{i, j\}$
X-Axis : $i = (1, 0)$
Y-Axis : $j = (0, 1$)
Alternate Basis Vector : $[\vec v]_\beta$

Ex.
$$\displaylines{\vec v = (5, 3) \\ = 5i + 3j}$$

Let's redefine the **Basis**:
$$\displaylines{\beta = \{\vec x, \vec w\}\\
\vec x = (2, 1)\\
\vec w = (1, 1)\\
[\vec v]_\beta = \left[\begin{array}{c}2 \\ 1\end{array}\right]}$$

We can define $A\vec x = b$  as:
$$\displaylines{\left[\begin{array}{cc}2 & 1 \\ 1 & 1\end{array}\right][\vec v]_\beta = \left[\begin{array}{c}5 \\ 3\end{array}\right]\\

\left[\begin{array}{cc|r}2 & 1 & 5 \\ 1 & 1 & 3\end{array}\right] \begin{aligned}\;RREF \\ ==\Longrightarrow \end{aligned} \left[\begin{array}{cc|r}1 & 0 & 2 \\ 0 & 1 & 1\end{array}\right]\\

∴[\vec v]_\beta = \left[\begin{array}{c}2 \\ 1\end{array}\right]}$$

Finally, we can find $[\vec v]_\beta$ with any given vector $\vec v$ such that :
$$[\vec{v}]_\beta = A^{-1}\vec{v}$$


---
##### Transformation Matrix For A Basis
Transformation Formula for Standard Basis:
$T(\vec{x}) = A\vec x$

Transformation Formula for Alternate Basis:
$[T(\vec{ x})]_\beta = M\vec x$ where, $C[\vec x]_\beta = \vec x$, and $M = C^{-1}AC$
$M = Transformation\; Matrix\; for\; an\; Alternate\; Basis$
$C = Change\; of\; Basis\; Matrix$

$$\displaylines{\begin{array}{ccc}
Domain & \;  &Codomain \\
\vec{x} & \begin{aligned} \longrightarrow^T_{A}\end{aligned} & T(\vec{x})  \\ \\
C^{-1}\downarrow \;\;\; & \; & \;\;\;\downarrow C^{-1} \\ \\
[\vec{x}]_{\beta} & \begin{aligned} \longrightarrow^T_{M}\end{aligned} & [T(\vec{x})]_{\beta}
\end{array}}$$


Ex.
$$\displaylines{T(\vec{x}) = \left[\begin{array}{cc}
1 & 0 \\ 2 & -2
\end{array}\right]\vec{x}, \;\;
\beta = span(\left[\begin{array}{c} -1 \\ 0 \end{array}\right],
\left[\begin{array}{c} 2 \\ -3 \end{array}\right]) \\
[\vec{x}]_{\beta} = (1, 3), \;\; C = \left[\begin{array}{cc} -1 & 2 \\ 0 & -3 \end{array}\right]\\ \\
To\; Find\; M:\\
C^{-1} = \left[\begin{array}{cc|rr} -1 & 2 & 1 & 0 \\ 0 & -3 & 0 & 1 \end{array}\right]\begin{aligned}\;RREF \\ ==\Longrightarrow \end{aligned} \left[\begin{array}{cc|rr} 1 & 0 & -1 & -\frac{2}{3} \\ 0 & 1 & 0 & -\frac{1}{3} \end{array}\right]\\ \\
Now \;we \;have: \\
C = \left[\begin{array}{cc} -1 & 2 \\ 0 & -3 \end{array}\right],\; C^{-1}=\left[\begin{array}{cc} -1 & -\frac{2}{3} \\ 0 & -\frac{1}{3} \end{array}\right] \\ \\
Calculate\; M=C^{-1}AC:\\
M=\left[\begin{array}{cc} -1 & -\frac{2}{3} \\ 0 & -\frac{1}{3} \end{array}\right]
\left[\begin{array}{cc} 1 & 0 \\ 2 & -2 \end{array}\right]
\left[\begin{array}{cc} -1 & 2 \\ 0 & -3 \end{array}\right] \\
= \left[\begin{array}{cc} \frac{7}{3} & \frac{-26}{3} \\ \frac{2}{3} & \frac{-10}{3} \end{array}\right] = \frac{1}{3} \left[\begin{array}{cc} 7 & -26 \\ 2 & -10 \end{array}\right]\\ \\
Let's\; Calculate\; [T(\vec{x})]_{\beta}:\\
[T(\vec{x})]_{\beta} = \frac{1}{3} \left[\begin{array}{cc} 7 & -26 \\ 2 & -10 \end{array}\right]\left[\begin{array}{c} 1 \\ 3 \end{array}\right]\\
=\frac{1}{3} \left[\begin{array}{cc} 7-78 \\ 2-30 \end{array}\right]\\ 
=\left[\begin{array}{cc} \frac{-71}{3} \\ \frac{-28}{3} \end{array}\right]}$$
