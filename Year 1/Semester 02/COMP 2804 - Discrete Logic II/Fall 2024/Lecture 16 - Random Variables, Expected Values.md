#### Random Variable

**Definition :**
	A random variable is a function $X:S \rightarrow \mathbb{R}$, where $S$ is a sample space.


Example : Rolling two dice
	$S = \{(i, j) : i, j \in  \{1, 2, 3, 4, 5, 6\}\}$
	$P(x) = \frac{1}{36}$
	$W(i, j) = i + j$


Example : Flip three coins
	$S = \{\text{HHH, HHT, HTH, HTT, THH, THT, TTH, TTT}\}$
	$P(x) = \frac{1}{8}$
	$X(w) = \text{"The number of heads"}$
$$\displaylines{X(HHH) = 3 \\
X(HHT) = X(HTH) = X(THH) = 2 \\
X(HTT) = X(THT) = X(TTH) = 1 \\
X(TTT) = 0 \\ \\
P(x = 0 ) = \frac{1}{8} \\
P(x = 1) = \frac{3}{8} \\
P(x = 2) = \frac{3}{8} \\
P(x=3) = \frac{1}{8}}$$


---
#### Independent Random Variables

**Definition :**
	Two random variables, X and Y, are independent if, for every $x, y \in \mathbb{R}$ : $$P(X = x \text{ and } Y=y) = P(X =x) ·P(Y=y)$$


Example : Using the coin example above.
$$\displaylines{P(X = 2 \text{ and } Y = 1) = P(\{THH, HTH, HHT\}\cap \{HHH, TTT\}) \\
P(\varnothing) = 0 \ne \frac{3}{8} · \frac{2}{8} = P(X = 2) · P(Y=1) \\ \\
∴ \text{X and Y are not independent}}$$


Example : Random variables that are independent

Lets define a new random variable :
	$Z = \left\{ \begin{array}{rcl} 1 & \text{if first coin is H} \\ 0 & \text{ otherwise} \end{array} \right.$
$$\displaylines{P(Y = 0 \text{ and } Z = 0) = P(\{HHT, HTH, HTT, THH, THT, TTH\}) \cap P(THH, THT, TTH, TTT) \\
P(\{THH, THT, TTH\}) = \frac{3}{8} \\ P(Y = 0) · P(Z = 0) = \frac{6}{8} · \frac{4}{8} = \frac{24}{64} = \frac{3}{8} \\ \\
P(Y = 0 \text{ and } Z= 1) \dots \\
P(Y = 1 \text{ and } Z = 0) \dots \\
P(Y = 1 \text{ and } Z = 1) \dots \\ \\
∴ \text{ Y and Z are independent random variables}}$$



---
#### Sequence of Random Variables

**Definition :** 
	A sequence of random variables $X_{1},\dots, X_{n}$ is pairwise mutually independent if for every $X_{1}, \dots, X_{n} \in \mathbb{R}$ the event $X_{1} = x_{1}, \dots, X_{n} = x_{n}$ are pairwise mutually independent.



---
#### The Expected Value

**Definition :**
	The expected value (mean) of a random variable $X$ is $$E(X) = \sum X(\omega) · P(\omega) = \sum P(X =x)x$$


Example : Toss a coin

$X(\omega) = \left\{ \begin{array}{tcl}1 & \text{if } \omega \text{ is H} \\ 0 & \text{if } \omega \text{ is T} \end{array} \right.$
$S = \{H, T\}$
$P(\omega) = \frac{1}{2}$
$$\displaylines{E(X) = X(H)·P(H) + X(T)·P(T) \\
= 1· \frac{1}{2} + 0· \frac{1}{2} \\
= \frac{1}{2}}$$

Example : Roll a six-sided die
$S = \{1, 2, 3,4,5,6\}$
$P(\omega) = \frac{1}{6}$
$X(i) = i$
$$\displaylines{E(X) = 1· \frac{1}{6} + 2 · \frac{1}{6} + 3· \frac{1}{6} + 4· \frac{1}{6} + 5· \frac{1}{6} + 6· \frac{1}{6} \\
=3.5}$$


Example : Rolling two dice
$S = \{(i, j) : i, j \in \{1, 2, 3, 4, 5, 6\}\}$
$P(\omega) = \frac{1}{6}$
$X(i, j) = i + j$
$$\displaylines{E(X) = \frac{1}{36}(2 + 3 + 3 + 4 + 4 + 4 + \dots + 11 + 11 + 12) = 7 \\
=2· \frac{1}{36} + 3· \frac{2}{36} + 4 · \frac{3}{36} + \dots + 11· \frac{2}{36} + 12· \frac{1}{36} = 7}$$



---
#### Linearity Of Expectation

**Definition :**
	For **any** two random variables, $X$ and $Y$, the $E(X+Y) = E(X) + E(Y)$


For any sequence of random variables $X_{1}, \dots, X_{n}$ : $$E(X_{1} + \dots + X_{n}) = E(X_{1}) + \dots + E(X_{n})$$
