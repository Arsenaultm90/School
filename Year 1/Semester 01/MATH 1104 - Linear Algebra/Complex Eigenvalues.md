Let $$\displaylines{\begin{aligned}A =\end{aligned}\left[\begin{array}{cc} 1 & -2\\ 1 & 3 \end{array}\right]}$$
a) Find Eigenvalues of A.
b) Diagonalize A, if possible.

a)
1. Find Characteristic Polynomial
	$A - \lambda I = \left[\begin{array}{cc}1-\lambda -2 \\ 1 3-\lambda \end{array}\right]$
	$det(A-\lambda I) = (1 - \lambda)(3-\lambda) + 2$
	$= 3 - \lambda - 3\lambda + \lambda^2 + 2$
	$= \lambda^2 -4\lambda + 5$
	∴The characteristic equation is
		$\lambda^2 -4\lambda + 2 = 0$

2. Find The Roots
	$\lambda_{1} = 2 + i,\; \lambda_{2} = 2-i$

3. $\lambda_1 = 2+i$
	$(A-(2+i)I)x = 0$
$$\displaylines{\begin{aligned}A =\end{aligned}\left[\begin{array}{cc|r} 1-(2+i) & -2 & 0\\ 1 & 3-(2+i) & 0 \end{array}\right] \approx \left[\begin{array}{cc|r} 1 & 1-i & 0\\ 0 & 0 & 0 \end{array}\right]}$$
	$x_2$ is a free variable
	$x_1 = -(1-i)x_{2} = (-1+i)x_{2}$

4. $x = \left[\begin{array}{c}x_{1} \\ x_{2} \end{array}\right] = x_{2}\left[\begin{array}{c}-1+i \\ 1 \end{array}\right]$

5. Eigenspace
	$$E_{2+i} = span\left\{\left[\begin{array}{c}-1+i \\ 1 \end{array}\right]\right\}$$
6. Basis For $E_{2+i}$
	$$\left\{V_{1} = \left[\begin{array}{c}-1+i \\ 1 \end{array}\right]\right\}$$
	Repeat for $\lambda_2$

b)
1. $A = PDP^{-1}$, where
	$$\displaylines{\begin{aligned}P =\end{aligned}\left[\begin{array}{cc} -1+i & -1-i\\ 1 & 1\end{array}\right] \; AND \; D = \left[\begin{array}{cc|r} 2+i & 0\\ 0 & 2-i \end{array}\right]}$$

