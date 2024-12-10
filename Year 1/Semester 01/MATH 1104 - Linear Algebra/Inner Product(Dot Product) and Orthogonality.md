The **Inner Product** is a way to multiply two vectors together to get a scalar, and it measures how much one vector "overlaps" or "aligns" with another and it satisfies key properties like linearity, symmetry, and positive definiteness.

Definition: Let $$\displaylines{u = \left[\begin{array}{c}u_{1} \\ u_{2} \\ \vdots \\ u_{n}\end{array}\right] \; AND \; v = \left[\begin{array}{c}v_{1} \\ v_{2} \\ \vdots \\ v_{n}\end{array}\right] \; in \; {\rm I\!R}^n. }$$
	The inner product(dot product) of $u$ and $v$ is:
		$$\displaylines{u · v = u^T · v = \left[\begin{array}{cccc}
u_{1} \; u_{2} \; \dots \; u_{3}\end{array} \right]\left[\begin{array}{c}
v_{1} \\ v_{2} \\ \vdots \\ v_{3}\end{array} \right] = u_{1}v_{1} + u_{2}v_{2} + \dots + u_{n}v_{n}}$$

 Example: Let $u = \left[\begin{array}{c}3 \\ -1\\ -5 \end{array}\right]$ and $v = \left[\begin{array}{c}6 \\ -2\\ 3\end{array}\right]$ in $\mathbb{R}^3$.
 $$\displaylines{u·v = u^Tv = \left[\begin{array}{c}3 & -1 & -5 \end{array}\right]\left[\begin{array}{c}6 \\ -2\\ 3 \end{array}\right]\\
 = 3·6+(-1)·(-2)+(-5)·3\\
 =18 +2 - 15\\
 =5}$$
 This tells us how well **aligned** the vectors are to each other, scaled by the magnitude of the vectors. Can thing of it as a scalar value.
 
NOTE: 
	$u·v = u^Tv \neq uv^T$. 
	$uv^T$ is a matrix and its call the **Outer Product**. 

---
##### The Length(norm) Of A Vector

Definition:
$$||v|| = \sqrt{ v·v }$$

Example: Let $u = \left[\begin{array}{c}1\\-1\end{array}\right]$
$$||u|| = \sqrt{ (1)^2+(-1)^2 } = \sqrt{ 2 }$$

NOTE:
	For all $v$ in $\mathbb{R}^n$ we have $||v|| > 0$ and $||v||^2 = v·v$


If $||u|| = 1$, then it is a **Unit Vector**.

Example: Let $v = \left[\begin{array}{c}\frac{1}{2} \\ -\frac{1}{2} \\ \frac{1}{2} \\ -\frac{1}{2}\end{array}\right]$

$$\displaylines{||v|| = \sqrt{ v·v } = \sqrt{ (\frac{1}{2})^2 +(-\frac{1}{2})^2 + (\frac{1}{2})^2 +(-\frac{1}{2})^2}\\
=\sqrt{ \frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{4} }\\ = 1}$$

Otherwise, if $||v|| \neq 1$, we can normalize it.

Example: Let $v = \left[\begin{array}{c}2 \\ -3 \\1\end{array}\right]$
$$\displaylines{||v|| = \sqrt{ 2^2 + (-3)^2 + 1^2 }\\ =\sqrt{ 4 + 9 + 1 }\\=\sqrt{ 14 } \neq 1}$$
Now we can normalize with $v = \frac{v}{||v||}$.$$\displaylines{v = \frac{1}{\sqrt{ 14 }}\left[\begin{array}{c}2 \\ -3 \\1\end{array}\right]\\
= \left[\begin{array}{c}\frac{2}{\sqrt{ 14 }} \\ -\frac{3}{\sqrt{ 14 }} \\ \frac{1}{\sqrt{ 14 }} \end{array}\right]}$$
---
##### Distance Between Vectors
**Definition:** Let $u$ and $v$ be two vectors in $\mathbb{R}^n$. The distance between $u$ and $v$ is the length of the vector $u-v$. That is: $$dist(u,v) = ||u-v||$$
Example: Let $u = \left[\begin{array}{c}1 \\ 2 \\ -1\end{array}\right]$ and $v=\left[\begin{array}{c}2 \\ 1 \\ 1\end{array}\right]$ in $\mathbb{R}^3$.
$$\displaylines{dist(u, v) = \left[\begin{array}{c}1 \\ 2 \\ -1\end{array}\right]-\left[\begin{array}{c}2 \\ 1 \\ 1\end{array}\right]\\
=\left|\left|\left[\begin{array}{c}-1 \\ 1 \\ -2\end{array}\right]\right|\right|\\
=\sqrt{ (-1)^2 + (1)^2 + (-2)^2 }\\
=\sqrt{ 6 }}$$

---
##### Orthogonality Between Vectors
**Definition:** Let $u$ and $v$ be vectors in $\mathbb{R}^n$. Then $u$ and $v$ are said to be orthogonal(perpendicular) to each other, and denoted by $u \perp v$, if $u ·v = 0$.

Example: Let $u = \left[\begin{array}{c}1 \\ 2 \\ 1\end{array}\right]$, $v = \left[\begin{array}{c}1 \\ -1 \\ 1\end{array}\right]$, and $w = \left[\begin{array}{c}1 \\ 1 \\ 1\end{array}\right]$. Then, $$\displaylines{u·v = 1-2+1 = 0\\
u·w = 1+2+1 = 4}$$
We can see that $u$ and $v$ are orthogonal to each other but $u$ and $w$ are not.


Pythagorean Theorem:
![[Screenshot 2024-12-05 at 11.08.53 AM.png]]$$u \perp v = ||u+v||^2 = ||u||^2 + ||v||^2$$
Example: In the previous example we had $u = \left[\begin{array}{c}1 \\ 2 \\ 1\end{array}\right]$, $v = \left[\begin{array}{c}1 \\ -1 \\ 1\end{array}\right]$ and $u·v$ = 0.

So, the Pythagorean Theorem must hold. 
We have $||u+v||^2\;$: $$\displaylines{||u+v||^2 = \left|\left|\left[\begin{array}{c}2 \\ 1 \\ 2\end{array}\right]\right|\right|^2 \\= \left(\sqrt{ (2)^2 + (1)^2 + (2)^2}\right)^2 \\= (\sqrt{ 9 })^2 \\= 9}$$
And we have $||u||^2 + ||v||^2\;$: 
$$\displaylines{||u||^2 + ||v||^2 = \left|\left|\left[\begin{array}{c}1 \\ 2 \\ 1\end{array}\right]\right|\right|^2 + \left|\left|\left[\begin{array}{c}1 \\ -1 \\ 1\end{array}\right]\right|\right|^2 \\
= \left(\sqrt{ (1)^2 + (2)^2 + (1)^2 }\right)^2 + \left(\sqrt{ (1)^2 + (-1)^2 + (1)^2 }\right)^2\\
= (\sqrt{ 6 })^2 + (\sqrt{ 3})^2\\
= 6 + 3 \\ = 9}$$
---
##### Finding Vector That Is Orthogonal To Other Vectors

**Example:** Let $u = \left[\begin{array}{c}1 \\ 1\\ 1\end{array}\right]$ and $v = \left[\begin{array}{c}-1 \\ 1\\ 1\end{array}\right]$. Find a non-zero vector $w \in \mathbb{R}^3$ that is orthogonal to both $u$ and $v$. 

We are looking for a vector $w = \left[\begin{array}{c}x \\ y\\ z\end{array}\right] \in \mathbb{R}^3$ such that: $$\displaylines{u·w = 0\; and\; v·w = 0}$$
This gives use the equations: $$\displaylines{x+y+z = 0\\-x+y+z=0}$$
Create an augmented matrix: $$\displaylines{\left[\begin{array}{ccc|r}
1 & 1 & 1 & 0 \\ -1 & 1 & 1 & 0
\end{array}\right] = 
\left[\begin{array}{ccc|r}
1 & 0 & 0 & 0 \\ 0 & 1 & 1 & 0
\end{array}\right]}$$
The general solution is: $$w = \left[\begin{array}{c}x \\ y\\ z\end{array}\right] = \left[\begin{array}{c}0 \\ -z\\ z\end{array}\right]=z\left[\begin{array}{c}0 \\ -1\\ 1\end{array}\right]  $$
So, $w = \left[\begin{array}{c}0 \\ -1\\ 1\end{array}\right]$ is orthogonal to both $u$ and $w$.

---
##### Orthogonal Complement of A Subspace
**Definition:** Let $W$ we a subspace of $\mathbb{R}^n$.

The set of all vectors $u \in \mathbb{R}^n$ that are orthogonal to $W$ is called the Orthogonal Complement of $W$, and denoted by $W\perp \;$: $$W^\perp = \{u \in \mathbb{R}^n \;|\; u \perp W\}$$

---

The Angle Between Two Non-Zero Vectors
$$\cos \theta = \frac{u·v}{||u|| * ||v||}$$


