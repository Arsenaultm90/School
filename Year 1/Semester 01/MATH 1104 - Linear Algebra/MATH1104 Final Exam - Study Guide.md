System Of Linear Equations

Echelon Forms Of A Matrix

Vector Equations and Matrix Equations

Linear Independence Of Vectors

Application Of Linear Systems

Linear Transformations

Inverse Of A Matrix

Subspaces

Basis and Dimensions of a Subspace(Column Space and Null Space of a Matrix)

Rank and Nullity

Determinants

Applications of Determinants

Eigenvalues, Eigenvectors, and Matrix Diagonalization

Complex Numbers

Polar Form of a Complex Number (De Moivre's Theorem)

Complex Eigenvalues

Inner Product and Orthogonality

Orthogonal Sets and Orthogonal Matrices

Orthogonal Projections

Gram-Schmidt Orthogonalization Process



##### Things to Review:
General Solution - Represented as free variables so show all solutions to the system,
	 i.e X = $x_4$[1 2 4]
	 
Homogeneous Solution - Representation of the system in terms of just the free variables without the constants since the equations are set to 0. This includes finding the ker(T) which is just finding the homogeneous solution to the system.

Parametric vector form - The solution to the system in the form of $X = x_{4}\left[\begin{matrix}1 \\2 \\3 \end{matrix}\right]$

Vector form - The representation of Ax=b in the form of $x_{1}\left[\begin{matrix}1 \\2 \\3 \end{matrix}\right] + x_{2}\left[\begin{matrix}1 \\2 \\3 \end{matrix}\right] + x_{3}\left[\begin{matrix}1 \\2 \\3 \end{matrix}\right]$

Dot Products - 
Inverse Matrix - 
The Matrix of Linear Transformations - 
Transformation Matrix - 
	One-To-One(L.I. Pivot Columns) - Every vector in the domain is uniquely mapped to a vector in the codomain.
	Onto(Pivot Rows = m) - Every vectors in the domain is mapped to.
	Range -Span of all the linearly independent columns of a matrix
Elementary Matrix - Identity matrix that you performed row operations on.
Inverse as a product of Elementary matrices - Multiply each elementary matrix together along with the original matrix, which gives us the identity matrix.

Determinants-
	-Det = 0 if any row or column is dependent.

Subspaces
	-Contains the zero vector
	-Closed under addition
	-Closed under scalar multiplication

Cofactorization
	-Finding determinants of matrices greater than 2x2
	-Finding $x_{3}$ or $b_{ij}$ 

Eigenvalues, Eigenvectors, Eigenspaces
Find eigenvalues:
	$det(A-ƛI)$
Find eigenvectors
Find eigenspace

Matrix Diagonalization
$A = PDP^{-1} \Rightarrow AP = PD$
$P$ - The matrix of the eigenvectors that span the Eigenspace.
$D$ - The matrix of the eigenvalues scalar to the identity matrix.

Complex Numbers
	Polar Form and De Moivre's Theorem
	
Roots
Solution to the matrix


### Long Answer Questions
##### Solving Systems of Equations
1. **Augmented Matrix:**
	From system of equations.
	
2. **Basic and Free Variables:**
	Basic - Pivot Columns
	Free - Non-Pivot Columns

3. **General Solution:**
	$x = x_{p} + x_{h}$ | $x_{p}$ - Particular Solution(Constant Vector), $x_{h}$ - Homogeneous Solution(Free Variables)
	Turn Matrix into RREF and and solve the system of equations.
	Write in parametric vector form.

4. **Homogeneous Solution:**
	Set equation equal to 0 and solve by RREF Matrix or by system of equations.


##### Linear Transformation
1. **Standard Matrix for T:**
	Given by the system of equations.

2. **Basis for ker(T):**
	Zero vector or find free variables from RREF

3. **Basis for range(T):**
	Where we have pivot columns in RREF, the vectors in the original matrix make the range.

4. **Invertibility:**
	Square Matrix, Non-Zero Determinant, No Free Variables(Full Rank)

5. **One-To-One:**
	Every vector 'b' in $R^m$ has, at most, one solution vector 'x' in $R^n$.
	The rank of the matrix is equal to the number of columns in the matrix.

6. **Onto:**
	Every vector 'b' in $R^m$ has, at least, one solution vector 'x' in $R^n$. 
	The rank of the matrix is equal to the number of rows in the matrix.

7. **Non-Zero Solution Vector:**
	Solve system of equations and set any free variables to 0. The constant vector is the solution.


##### Basis, Col(A), Nul(A)
1. **Basis for Col(A):**
	RREF to find pivot columns.
	Respective columns in original matrix are the span of Col(A).

2. **Basis for Nul(A):**
	Solve system of equations to find free variables.

3. **Rank - Nullity Theorem:**
	Rank of Col(A) + Nullity of Nul(A) = # of columns


Determinants of A Matrix


##### Find Inverse of A Matrix
1. 2x2 Formula:
	$\frac{1}{\det(A)}Adj(A)$

2. **3x3 and higher solution:**
	$[A | I] \Rightarrow [I|A]$
	Cofactor Expansion


##### Cramer's Rule
	$x_{i} = \frac{\det(A_{i})}{\det(A)}$
	We replace the $i^{th}$ column with the vector 'b' and calculate the determinant.


##### $ij$-Cofactor of A
1. $C_{ij} = \det(A_{ij})$
2. $b_{ij} = \frac{C_{ji}}{\det(A)}$
	NOTE: Let $A^{-1} = b_{ij}$
	

Eigenvalues, Eigenvectors, Eigenspaces



Orthogonality
	1. Every vector dot product within the set must equal 0:  $\vec{u_{1}} · \vec{u_{2}} = 0$
	2. Find projection of v onto W
	3. Find vector orthogonal to the subspace: 
		u = v - Projv, where:
		u = Orthogonal Vector
		v = original vector
		Projv = v projected onto subspace
		Projv = X-Axis of v
		u = Y-Axis of v
	4. 