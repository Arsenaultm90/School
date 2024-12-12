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
Remember: $$\displaylines{Proj_{v}\vec{x} = \frac{v_{n}·u_{n}}{u_{n}·u_{n}}u_{n}}$$


---
##### Gram-Schmidt Process For Change Of Basis
**Formula:**
$$\displaylines{\text{First Vector}\\
\vec{u_{1}} = \vec{v_{1}}\\\ \\
\text{Projected Vector Onto Subspace}\\
Proj_{u}\vec{v_{n}} = \frac{\vec{v_{n}}·\vec{u_{1}}}{\vec{u_{1}}·\vec{u_{1}}}\vec{u_{1}} + \dots + \frac{\vec{v_{n}}·\vec{u_{n}}}{\vec{u_{n}}·\vec{u_{n}}}\vec{u_{n}}\\ \\
\text{Vector Orthogonal To Subspace}\\
\vec{u}_{n} = \vec{v}_{n}-Proj_{u}\vec{v_{n}}\\ \\
\text{Distance From}\; \vec{v}\; \text{To Subspace}\\
||\vec{v}|| = \sqrt{ (v_{11})^2 +\dots+(v_{n1})^2}
}$$

Ex.


---


