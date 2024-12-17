**Definitions:**
Functions : $f(x)$
Inputs : Set A (Domain of $f$)
Outputs : Set B (Codomain of $f$)

If $f$ is a function from A to B, then it is written as:
$f$ : A $\rightarrow$ B

$f(a) = b$, then $b$ is the **image** of $a$ and $a$ is a **pre-image** of $b$.
The set of all the images of elements from Set A is the **range** of $f$.

$S$ = Subset of the Domain
Image of $S$ = Subset of Codomain that contains the image of every element in the subset $S$.


---

##### Injection
Function $f$ is an Injection or Injective function if: $$\displaylines{\forall x \; \forall y \; f(x) = f(y) \rightarrow x = y }$$
Where:
	Every element in the **range**(return) has EXACTLY ONE **pre-image**(arg) that maps to it. 
	Elements in **range** and **pre-image** are one-to-one.

For $f(x) = 2x + 5$, prove that $f(x)$ is an Injective function.
Prove:
	1. $f(x) = f(y)$
	2. $f(x) = 2x + 5$
	3. $f(y) = 2y + 5$
	4. $2x + 5 = 2y + 5$
	5. $2x = 2y$
	6. $x = y$

For $g(x) = |x|$, disprove that $g$ is an Injective function.
Let $x$ = 1, $y$ = -1.
Disprove:
	1. $(g(x) = g(y)) \rightarrow (x = y)$   Initial Assumption
	2. $\neg (g(x) = g(y)) \lor (x = y)$ (1)Implication Equivalence
	*Proof By Cases*
	Case 1 : $\neg (g(x) = g(y))$
	3. $g(x) = |x| = |1| = 1$         Definition of $g$
	4. $g(y) = |y| = |-1| = 1$     Definition of $g$
	5. $g(x) = g(y)$
	6. $(g(x) = g(y)) \land \neg (g(x) = g(y))$  (5, Case 1) Conjunction
	7. False                                 (6)Complement Law
	Case 2 : x = y
	8. $\neg (x = y)$
	9. $\neg (x = y) \land (x = y)$          (8, Case 2) Conjunction
	10. False                              (9) Complement Law


---

##### Surjection
Function $f$ is a Surjection or Surjective function if: $$\displaylines{\forall b \in B \;\ \exists a \in A \;\ f(a) = b}$$
Where:
	Every element of the Codomain has at least one **pre-image**. $(Range = Codomain)$

Prove a function is Surjective:
	Start with an arbitrary element $b \in B$ and show that there exist $a \in A$ such that $f(a) = b$
	Example: $f(x) = 2x + 5$
	1. $f(a) = 2a + 5$
	2. $2a + 5 = b$
	3. $a = \frac{b - 5}{2}$
	4. $f(\frac{b - 5}{2}) = 2 (\frac{b - 5}{2}) + 5$  (1)
	5. $f(\frac{b-5}{2}) = b$                  (5)
	

Prove a function is NOT Surjective:
	Find a specific element $b \in B$ such that there does not exist $a \in A$ such that $f(a) = b$
	Example: $g(x) = |x|$
	1. $\exists x \; (|x| = -1)$
	2. $\exists x (g(x) = -1)$


---


##### Bijection (Injection and Surjection)

Definition:
	Every element of the **domain** maps to a unique element of the **codomain**, and every element of the **codomain** is covered by some element of the **domain**.
	or
	Every element in the codomain is mapped to by, at most, one element in the domain.

If a function $f$ is a bijection then $f$ is invertible where:
	$f^{-1}(b) = a \leftrightarrow f(a) = b$

To prove that the invertibility of a function requires that it is an Injection and that it is a Surjection, we can provide proof by contradiction. 

Injective : $\forall x \; \forall y \; f(x) = f(y) \rightarrow x = y$
Contradiction :  $\neg \forall x \; \forall y \; f(x) = f(y) \rightarrow x = y$
Proof : $f^{-1}(u) = i \land f^{-1}(u) = j \land i = j$ means  that $f^{-1}$ is not a function.

Surjective : $\forall b \in B \;\ \exists a \in A \;\ f(a) = b$
Contradiction : $\neg \forall b \in B \;\ \exists a \in A \;\ f(a) = b$
Proof : $\exists b \in B \;\;\ \forall a \in A \; f(a) \neq b$ means that $f^{-1}$ is not a function.


---


##### Function Composition

Given functions $f$ and $g$, the output of one can be the input to the other to create a new function.
Let $f : B \rightarrow C$ and $g : A \rightarrow B$

Composition $f \circ g$ ($f$ follows $g$) is $f \circ g : A \rightarrow C$ $$\displaylines{(f \circ g)(x) = f(g(x))}$$
Example:
	$$\displaylines{f(x) = 4x + 1 \\
	g(x) = 5x + 3 \\ \\
	(f \circ g)(x) = f(g(x)) \\
	= f(5x + 3) \\
	= 4(5x + 3) + 1 \\
	= 20x + 13}$$


Composition between an Invertible Function and its Inverse:
$(f \circ f^{-1})(x) = x$

