Rectangular Form: $z = a + ib$
Polar Form: $r(cosθ+isinθ)$
Let $θ$ be the angle between the positive real axis and the point $z$, $-\pi < θ ≤ \pi$.
The angle $θ$ is called the argument of $z$, and denoted by $θ = argz$.

![[Screenshot 2024-11-27 at 10.13.24 AM.png]]

Note: $$\displaylines{z = a + ib \\ = |z|cosθ + i|z|sinθ \\ = |z|(cosθ + isinθ) \\ = |z|cisθ \\ = |z|e^{iθ}}$$
Example:
Find the polar form of $z = 1 + i$

Solution:
$$|z| = \sqrt{ 1^2 + 1^2 } = \sqrt{ 2 }$$
$$\displaylines{\left[\begin{array}{ccc|r} \cosθ = \frac{a}{|z|} = \frac{1}{\sqrt{ 2 }} = \frac{\sqrt{ 2 }}{2} \\ \sinθ = \frac{b}{|z|} = \frac{1}{\sqrt{ 2 }} = \frac{\sqrt{ 2 }}{2} \end{array}\right]\begin{aligned} \Rightarrow θ = \frac{\pi}{4} \end{aligned}}$$
∴
	$z = 1 + i = \sqrt{ 2 }(\cos\frac{\pi}{4}+i\sin(\frac{\pi}{4})) = \sqrt{ 2 }cis(\frac{\pi}{4}) = \sqrt{ 2 }e^{i\frac{\pi}{4}}$

Note:
	The sign of $cosθ$(x-Axis) and $sinθ$(y-Axis) informs the quadrant of the angle. 
	(+)(+) = 1st Quadrant
	(-)(+) = 2nd Quadrant
	(-)(-) = 3rd Quadrant
	(+)(-) = 4th Quadrant

![[Screenshot 2024-12-02 at 8.32.45 AM.png]]

---
##### Complex Multiplication And Division In Polar Form

Let $z_1 = |z_1|cisθ_{1}$ and $z_2 = |z_{2}|cisθ_{2}$
	Then, $$\displaylines{z_{1} · z_{2} = |z_{1}| · |z_{2}| ·cis(θ_{1} + θ_{2}) \\ \frac{z_{1}}{z_{2}} = \frac{|z_{1}|cisθ_{1}}{|z_{2}|cisθ_{2}} = \frac{|z_{1}|}{|z_{2}|}cis(θ_{1} - θ_{2}) \\ \overline z = |z_{1}|cis(-θ_{1})}$$
Example: Let $z = cis\frac{\pi}{2}$ and $w = 2cis(\frac{-\pi}{3})$
Find $z · w$, $\frac{z}{w}$, $\overline z$, and $\overline w$

$z · w = cis(\frac{\pi}{2}) · 2cis(\frac{-\pi}{3}) = 2cis(\frac{\pi}{2} - \frac{\pi}{3}) = 2cis(\frac{\pi}{6}) = 2(\frac{\sqrt{ 3 }}{2} + i\frac{1}{2}) = \sqrt{ 3} + i$
$\frac{z}{w} = \frac{1}{2}cis(\frac{\pi}{2} + \frac{\pi}{3}) = \frac{1}{2}cis(\frac{5\pi}{6}) = \frac{1}{2}(\frac{-\sqrt{ 3 }}{2} + i\frac{1}{2}) = \frac{-\sqrt{ 3 }}{4} + i\frac{1}{4}$
$\overline z = cis(-\frac{\pi}{2}) = -i$
$\overline w = 2cis(-\frac{-\pi}{3}) = 2(\frac{1}{2} + i\frac{\sqrt{ 3 }}{2}) = 1 + i\sqrt{ 3 }$


---

##### De Moivre's Theorem For Powers Of A Complex Number
Let $n$ be a positive integer. Let $z$ = $|z|(\cosθ + i\sinθ)$
	Then, $$z^n = (|z|(\cosθ + i\sinθ))^n = |z|^2(\cos nθ +i\sin nθ)$$
Example: Let $z = 1+i$. Find $z^{20}$. Express the answer in standard form $a+ib$.
Solution:
	1. Find magnitude $|z|$:
		$|z| = \sqrt{ 1^2 + 1^2 } = \sqrt{ 2 }$
	2. Find Theta(θ):
		$θ = tan^{-1}(\frac{1}{1}) = \frac{\pi}{4}$ 
	3. Express in Polar Form:
		$\sqrt{ 2 }(\cos(\frac{\pi}{4}) + i\sin(\frac{\pi}{4}))$
	4. $$\displaylines{z^{20} = \sqrt{ 2 }^{20}(\cos(\frac{\pi}{4}) + i\sin(\frac{{ \pi }}{4}))^{20} \\ 
	   z^{20} = \sqrt{ 2 }^{20}(\cos(\frac{20\pi}{4}) +i\sin(\frac{5\pi}{4})) \\ z^{20} = 2^{10}(\cos(5\pi)+i\sin(5\pi)) \\
	   z^{20} = 2^{10}(\cos(\pi) +i\sin(\pi)) \\
	   z^{20} = 2^{10}(-1 + i·0)\\
	   z^{20} = -2^{10}\\
	   z^{20} = -1024}$$
Alternatively, $$\displaylines{(1+i)^2 = 2i \Longrightarrow (1+i)^4 = (2i)^2 = -4\\
(1+i)^{20} = ((1+i)^4)^5 = -4^5 = -2^{10} = -1024 }$$

