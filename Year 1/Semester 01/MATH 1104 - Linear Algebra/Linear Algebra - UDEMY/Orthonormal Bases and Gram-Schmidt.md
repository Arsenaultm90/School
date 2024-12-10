Orthonormal Sets:
1. All vectors are normalized (Unit vector  $||v_1||^2 = 1$)
2. All vectors are orthogonal  ($v_1 · v_2 = 0$)


---
##### Orthonormal Basis
Vector Set:$$\displaylines{\vec{v}_{1} = (0, 0, -1) \\
\vec{v}_{2} = (\frac{1}{\sqrt{ 2 }}, \frac{1}{\sqrt{ 2 }}, 0)\\
\vec{v}_{3} = (\frac{1}{\sqrt{ 2 }}, -\frac{1}{\sqrt{ 2 }}, 0)}$$
Orthogonality:$$\displaylines{\vec{v}_{1} · \vec{v}_{2} = 0 + 0 + 0 = 0\\
	\vec{v}_{1} · \vec{v}_{3} = 0 + 0 + 0 = 0\\
	\vec{v}_{2} · \vec{v}_{3} = \frac{1}{2}, -\frac{1}{2} + 0 = 0}$$
Normalization:$$\displaylines{||\vec{v}_{1}||^2 = 0 + 0 + 1 = 1\\
	||\vec{v}_{2}||^2 = \frac{1}{2} + \frac{1}{2} + 0 = 1\\
	||\vec{v}_{3}||^2 = \frac{1}{2} + \frac{1}{2} + 0 = 1}$$
∴ We have an **Orthonormal** set.

Orthogonal Matrix:
	Orthogonal if matrix is square, otherwise, Orthonormal.
$$\displaylines{\left[\begin{array}{ccc}
0 & \frac{1}{\sqrt{ 2 }} & \frac{1}{\sqrt{ 2 }}\\
0 & \frac{1}{\sqrt{ 2 }} & -\frac{1}{\sqrt{ 2 }}\\
-1 & 0 & 0
\end{array}\right]
[\vec{x}]_{\beta} =
\left[\begin{array}{c}
5 \\ 2 \\ -3
\end{array}\right]}$$
	Now, we can take the dot product of the matrix with the vector.
$$\displaylines{[\vec{x}]_{\beta} = \left[\begin{array}{ccc}
0 & 0 & 3 \\
\frac{5}{\sqrt{ 2 }} & \frac{2}{\sqrt{ 2 }} & 0 \\
\frac{5}{\sqrt{ 2 }} & -\frac{2}{\sqrt{ 2 }} & 0
\end{array}{}\right] = \left[\begin{array}{c}
3 \\ \frac{7}{\sqrt{ 2 }} \\ \frac{3}{\sqrt{ 2 }}
\end{array}\right]}$$
	We have found our **Alternate Basis**.


---
##### Projection Onto An Orthonormal Basis
Remember: $$\displaylines{Proj_{v}\vec{x} = A(A^TA)^{-1}A^T \vec{x}\\
= AIA^T\vec{x}\\
= AA^T\vec{x}}$$
Using vectors from our previous problem:
$$ \left.\begin{array}{c}
\vec{v}_{1} = (0, 0, 1) \\ 
\vec{v}_{2} = (\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}}, 0)
\end{array} \right\} V$$
Now we set up our matrices: $$\displaylines{A= \left[\begin{array}{cc}
0 & \frac{1}{\sqrt{ 2 }} \\ 0 & \frac{1}{\sqrt{ 2 }} \\ 1 & 0
\end{array}\right], \; A^T= \left[\begin{array}{ccc}
0 & 0 & 1  \\ \frac{1}{\sqrt{ 2 }} & \frac{1}{\sqrt{ 2 }} & 0
\end{array}\right]}$$
$$\displaylines{AA^T = \left[\begin{array}{cc}
0 & \frac{1}{\sqrt{ 2 }} \\ 0 & \frac{1}{\sqrt{ 2 }} \\ 1 & 0
\end{array}\right]\left[\begin{array}{ccc}
0 & 0 & 1  \\ \frac{1}{\sqrt{ 2 }} & \frac{1}{\sqrt{ 2 }} & 0
\end{array}\right] \\
= \left[\begin{array}{ccc}
0 + \frac{1}{2} & 0+\frac{1}{2} & 0+0 \\
0+\frac{1}{2} & 0+\frac{1}{2} & 0+0 \\
0+0 & 0+0 & 1+0
\end{array}\right]\\
=\left[\begin{array}{ccc}
\frac{1}{2} & \frac{1}{2} & 0 \\
\frac{1}{2} & \frac{1}{2} & 0 \\
0 & 0 & 1
\end{array}\right]\vec{x}}$$

Now that we have the projection matrix, we can multiply it with a $\vec{x}$ to find the projected vector.
Let's say: $$\vec{x}=(1, 2 ,3)$$
Then: $$\displaylines{=\left[\begin{array}{ccc}
\frac{1}{2} & \frac{1}{2} & 0 \\
\frac{1}{2} & \frac{1}{2} & 0 \\
0 & 0 & 1
\end{array}\right]\left[\begin{array}{ccc}
1 \\
2 \\
3
\end{array}\right]\\
=\left[\begin{array}{ccc}
\frac{1}{2} + \frac{2}{2} + 0 \\
\frac{1}{2} + \frac{2}{2} + 0 \\
0 + 0 + 3
\end{array}\right]\\
Proj_{v}\vec{x}=\left[\begin{array}{ccc}
\frac{3}{2} \\
\frac{3}{2} \\
 3
\end{array}\right]}$$

---
##### Gram-Schmidt Process For Change Of Basis
**Formula:**
$$\displaylines{\vec{u} = \frac{\vec{v}}{||\vec{v}||}\\
\vec{w}_{2} = \vec{v}_{2}-(\vec{v}_{2}·\vec{u}_{1})\vec{u}_{1}\\
\vec{w}_{3} = \vec{v}_{3}-[(\vec{v}_{3}·\vec{u}_{1})\vec{u}_{1}+(\vec{v}_{3}·\vec{u}_{2})\vec{u}_{2}]}$$

Ex.
We have: $$\displaylines{V = span(\left[\begin{array}{c}
-1 \\ 1 \\0
\end{array}\right],\left[\begin{array}{c}
2 \\ 0 \\-1
\end{array}\right])}$$
Now we find the magnitude of $\vec{v}_{1}$: $$\displaylines{||\vec{v}_{1}|| = \sqrt{ 1+1+0 } = \sqrt{ 2 }}$$
We now need to normalize the vector using our formula: $$\displaylines{\vec{u}_{1} = \frac{1}{\sqrt{ 2 }}\left[\begin{array}{c}
-1 \\ 1 \\0
\end{array}\right] =
\left[\begin{array}{c}
\frac{-1}{\sqrt{ 2 }} \\ \frac{1}{\sqrt{ 2 }} \\0
\end{array}\right]}$$
We now need to replace $\vec{v}_{2}$ with a vector that is orthogonal to $\vec{u}_{1}$: $$\displaylines{\vec{w}_{2}= \vec{v}_{2}-(\vec{v}_{2}·\vec{u}_{1})\vec{u}_{1}\\
\vec{w}_{2} = \left[\begin{array}{c}
2 \\ 0 \\ -1
\end{array}\right]-(\left[\begin{array}{c}
2 \\ 0 \\ -1
\end{array}\right]·\left[\begin{array}{c}
\frac{-1}{\sqrt{ 2 }} \\ \frac{1}{\sqrt{ 2 }} \\0
\end{array}\right])\left[\begin{array}{c}
\frac{-1}{\sqrt{ 2 }} \\ \frac{1}{\sqrt{ 2 }} \\0
\end{array}\right]\\
= \left[\begin{array}{c}
2 \\ 0 \\ -1
\end{array}\right]-(-\frac{2}{\sqrt{ 2 }}+0+0)\left[\begin{array}{c}
\frac{-1}{\sqrt{ 2 }} \\ \frac{1}{\sqrt{ 2 }} \\0
\end{array}\right]\\
= \left[\begin{array}{c}
2 \\ 0 \\ -1
\end{array}\right]+\frac{2}{\sqrt{ 2 }}\left[\begin{array}{c}
\frac{-1}{\sqrt{ 2 }} \\ \frac{1}{\sqrt{ 2 }} \\0
\end{array}\right]\\
= \left[\begin{array}{c}
2 \\ 0 \\ -1
\end{array}\right]+\left[\begin{array}{c}
-1 \\ 1 \\0
\end{array}\right]\\
= \left[\begin{array}{c}
1 \\ 1 \\ -1
\end{array}\right]}$$
Now, we find the Magnitude:$$\displaylines{||\vec{w}_{2}||=\sqrt{ 1^2+1^2+(-1)^2 }\\ =\sqrt{ 3 }}$$
And finally, we normalize that vector to find the unit vector $\vec{u}_{2}$: $$\displaylines{\vec{u}_{2}=\frac{1}{\sqrt{ 3 }}\left[\begin{array}{c}
1 \\ 1\\ -1
\end{array}\right]\\
=\left[\begin{array}{c}
\frac{1}{\sqrt{ 3 }}\\ \frac{1}{\sqrt{ 3 }} \\ -\frac{1}{\sqrt{ 3 }}
\end{array}\right]}$$

---


