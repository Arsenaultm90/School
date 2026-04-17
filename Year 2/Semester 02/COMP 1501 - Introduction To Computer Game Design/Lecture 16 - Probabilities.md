Probability is a measurement of how likely some event is to occur.  
An important note: We always describe probability as a number between 0 and 1;  
	0 being impossible
	1 being definite.
$$\frac{\text{No. of event where A happens}}{\text{Total number of events}}$$

Example: Odd number on six-sided die $$P(odd) = \frac{|\{1, 2, 3\}|}{|\{1, 2, 3, 4, 5, 6\}|} = \frac{3}{6} = 50\%$$
**Independent Events**  
Two events are independent means that one happening will not affect the other.

If events A and B are independent, the probability of BOTH of these happening ($P(A \cap B)$) is the product of $P(A)$ and $P(B)$.

Example: Probability of both coins landing on “Heads” is: $$P(A \cap B) = P(A)P(B) = \frac{1}{2} · \frac{1}{2} = \frac{1}{4}$$

**Mutually Exclusive Events**
A and B are mutually exclusive if both CANNOT happen together.
The chance of either happening (P(A ∪ B)) is the sum of both.

Example: Rolling either a 4 or 5 on a six-sided die: $$P(A \cup B) = P(A) + P(B) = \frac{1}{6} + \frac{1}{6} = \frac{2}{6} = \frac{1}{3}$$

**Expected Value**
Expected value for a discrete variable $x$ is: $$E(x) = \sum x_{i}p_{i}$$
$x_{i}$ is the value attached to the $i^{th}$ outcome
$p_{i}$ is the probability of the $i^{th}$ outcome

Example:
Attacker: Roll 1d20, hits on 16+  
Weapon: Deals 1d6 damage  
Critical: On 20, deal 2*1d6 damage

$P(Hit) = \frac{4}{20} = 0.2$
$P(Crit) = \frac{1}{20} = 0.05$
$E(1d_{6}) = 1 · \frac{1}{6} + 2 · \frac{1}{6} + \dots = 3.5$
$E(Crit) = 7$
∴ $E(dmg) = 3.5(0.2) + 7(0.05) = 1.05$


