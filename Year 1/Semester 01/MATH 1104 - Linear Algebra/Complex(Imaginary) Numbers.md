Definition:
	$$\displaylines{i = \sqrt{-1} \\ i^2 = -1}$$
	∴ $i$ is a root of the quadratic equation:
	 $$z^2 + 1 = 0$$

Note: A complex(imaginary) number $z$ is of the form: $z = a + ib$, where $a, b$ 𝜖 $ℝ$
$a =$ Re $z$  is the real part of $z$, and $b =$ Im $z$ is the imaginary part of $z$.
ℂ = Set of all complex numbers


---

##### Addition Of Complex Numbers
Let $z = a + ib$ and $w = c + id$ be two complex numbers. Then, $$\displaylines{z + w = a + c + i(b+d) \\ z - w = a - c + i(b - d)}$$
	Example: Let $x = 1 - 4i$ and $w = 3 + 2i$$$\displaylines{z + w = 1 + 3 + i(-4 + 2) = 4 - 2i \\ z - w = 1 - 3 + i(-4 - 2) = -2 - 6i}$$

---

##### Multiplication Of Complex Numbers
Let $z = a + ib$ and $w = c + id$ be two complex number and let $t$ 𝜖 ℝ. Then, $$\displaylines{zw = (a + ib)(c + id) = ac - bd + i(ad + bc) \\ tz = t(a + ib) = ta + itb}$$
	Example: Let $z = 1 - 4i$ and $w = 3 + 2i$. Let us find $zw$ and $5z$. $$\displaylines{zw = (1 - 4i)(3 + 2i) = 3 + 2i - 12i -8i^2 = 3 - 10i -8(-1) = 11 -10i \\ 5z = 5(1-4i) = 5 - 20i}$$
	Or, we can use the above formula with $a = 1$, $b = -4$, $c = 3$, $d = 2$, and $t = 5$.


---

##### Conjugate And Modulus Of A Complex Number
Definition: Let $z = a + ib$ be a complex number. The **conjugate** of $z = a + ib$ is $$\displaylines{\bar{z} = a - ib}$$
and the **modulus** (absolute value) of $z$ is $$\displaylines{|z| = \sqrt(a^2 + b^2) = \sqrt(z · \bar{z})}$$
	Example: Let $z = 3 + 4i$ and $w = 1 - 2i$. Then, $\bar{z} = 3 - 4i$ and $\bar{w} = 1 + 2i$. And, $$\displaylines{|z| = \sqrt(3^2 + 4^2) = \sqrt(9 + 16) = 5,\\ |w| = \sqrt(1^2 + (-2)^2) = \sqrt(1 + 4) = \sqrt(5) \\\\ |\bar{z}| = \sqrt(3^2 + (-4)^2) = \sqrt(9 + 16) = 5,\\ |\bar{w}| = \sqrt(1^2 + 2^2) = \sqrt(1 + 4) = \sqrt(5)}$$
	We note that $|\bar{z}|$ = $|z|$, $\bar{z}$ = $z$ and $z · \bar{z}$ = $a^2 + b^2 = |z|^2$


Remark: Let $z = a + ib$. We have the following properties:$$\displaylines{z + \bar{z} = 2a = 2\; Re \; z, \\ z - \bar{z} = 2ib = 2i \; Im \; z.}$$
Remark: Let $z = a + ib$ and $w = c + id$. We have the following properties: $$\displaylines{|z · w| = |z| · |w|, \\ \overline{z · w} = \bar{z} · \bar{w}, \\ \overline{z + w} = \bar{z} + \bar{w}, \\ \overline{z - w} = \bar{z} - \bar{w}.}$$

---

##### Division Of Complex Numbers
Definition: $$\displaylines{\frac{z}{w} = \frac{a + ib}{c + id} = \frac{a + ib}{c + id} · \frac{c + id}{c + id} = \frac{x}{z} \pm \frac{y}{z}i}$$

Example: Let $z = 1 - 4i$ and $w = 3 + 2i$. Let us write $\frac{z}{w}$ in the standard form $a + ib$. $$\displaylines{\frac{z}{w} = \frac{1 - 4i}{3 + 2i} = \frac{1 - 4i}{3 + 2i} · \frac{3 + 2i}{3 + 2i} = \frac{3 - 2i - 12i + 8i^2}{9+4} = \frac{-5 - 14i}{13} = \frac{-5}{13} - \frac{14}{13}i}$$
Note: $$\displaylines{|z^1| = \frac{1}{|z|} \\ |\frac{z}{w}| = \frac{|z|}{|w|}}$$

---


##### Roots Of A Quadratic Equation In Complex Numbers

Let us find the roots of the quadratic equation $z^2 - 4z  + 5 = 0$. $$\displaylines{z = \frac {-b \pm \sqrt{b^2 -4ac}} {2a} = \frac {-(-4) \pm \sqrt{(-4)^2 -4·1·5}} {2·1} = \frac {-4 \pm \sqrt{16 - 20}} {2} \\ = \frac {4 \pm \sqrt{-4}} {2} = \frac {4 \pm 2\sqrt{-1}} {2} = 2 \pm i \\\\ ∴ z = 2-i, 2+i}$$
OR we can use completing the square: $$\displaylines{z^2 - 4z + 5 = (z - 2)^2 + 1 \\ (z - 2)^2 + 1 = 0 \\ (z - 2)^2 = -1 \\ z - 2 = \pm i \\ z = 2 \pm i \\ \\ ∴ z = 2 - i, 2 + i}$$

---

##### Systems Of Linear Equations With Complex Numbers

Example: Solve the following system of linear equations. $$\displaylines{z_{1} + iz_{2} - iz_{3} = i \\ iz_{1} - z_{2} - z_{3} = -1 + 2i \\ -z_{1} + (1-i)z_{2} - iz{3} = -i}$$
Solution: $$\displaylines{\left[\begin{array}{ccc|r} 1 & i & -i & i \\ i & -1 & -1 & -1 + 2i \\ -1 & 1-i & -i & -i \end{array}\right]\begin{aligned} R'_2 &= R_2 + (-i)R_1 \\ R'_3 &= R_3 + R_1 \end{aligned}}$$
$$\displaylines{\left[\begin{array}{ccc|r} 1 & i & -i & i \\ 0 & 0 & -2 & 2i \\ 0 & 1 & -2i & 0 \end{array}\right]\begin{aligned} R_2 \leftrightarrow R_3 \end{aligned}}$$
$$\displaylines{\left[\begin{array}{ccc|r} 1 & i & -i & i \\ 0 & 1 & -2i & 0 \\ 0 & 0 & -2 & 2i \end{array}\right]}$$
From the third row we have $-2 z_3 = 2i, which gives $$\displaylines{z_3 = -i}$$
From the second row we have $z_2 - 2iz_3 = 0$, which gives $$\displaylines{z_2 = 2iz_3 = 2i(-i) = 2}$$
From the first row we have $z_1 + iz_2 - iz_3 = i$, which gives $$\displaylines{z_1 = i - iz_2 + iz_3 = i - 2i + i(-i) = 1-i}$$
The solution of the system in vector form is: $$\displaylines{
\left[\begin{array}{c}
z_1 \\ z_2 \\ z_3
\end{array}\right]
=
\left[\begin{array}{c}
1 - i \\ 2 \\ -i
\end{array}\right]
}$$


