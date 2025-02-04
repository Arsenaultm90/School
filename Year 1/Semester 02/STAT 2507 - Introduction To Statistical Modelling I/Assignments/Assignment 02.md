STAT 2507 E
Matthew Arsenault
101288386

1.

![[Screenshot 2025-01-29 at 1.30.04 PM.png|500]]

a) The scatter plot suggests there is a positive correlation between sodium levels in the water and total dissolved salts. As the sodiums levels increase, the total dissolved salts tend to increase.

<div style='page-break-after: always;'></div>


b) Sample Covariance : $$\displaylines{\text{ Given :}
\sum x_{i} = 99.3,\;
\sum y_{i}= 14,396,\;
\sum x_{i}y_{i} = 149,379.2}$$
$$s_{xy} =\frac{\sum^{n}_{i=1}X_{i}Y_{i}-\frac{\left( \sum^{n}_{i=1}X_{i} \right)\left( \sum^{n}_{i=1}Y_{i} \right)}{n}}{n-1}$$$$\displaylines{s_{xy} = \frac{149379.2 - \frac{99.3 \times 14396}{11}}{11-1}
=\frac{149379.2-129956.6182}{10}
=\frac{19422.58182}{10}
=1942.258182}$$
Sample Correlation Coefficient : $$\displaylines{\text{Given : }\\ s_{x} = 3.676,\;s_{y} = 717.955 \\ \\r = \frac{s_{xy}}{s_{x}s_{y}} \\ \\
=\frac{1942.258182}{3.676 \times 717.955}
=\frac{1942.258182}{2639.20258}
\approx 0.735926146 }$$

c) Finding $y = mx +b$
$$\displaylines{m = r\frac{s_{y}}{s_{x}} \\ \\
=0.735926146\times \frac{717.955}{3.676}
\approx 143.7328226}$$
$$\displaylines{b = \overline{y}-m\overline{x} \\ \\
b = \frac{14396}{11}-143.7328226 \times \frac{99.3}{11}  \approx 11.2118834}$$
$$\displaylines{m = 143.7328226 \\
b = 11.2118834 \\ \\
∴y = 143.7328226x - 11.2118834}$$

<div style='page-break-after: always;'></div>


d)$$\displaylines{y = 143.7328225 \times 7.2 - 11.2118834 \\=1023.664439}$$

e)
Calculated Correlation Coefficient $\approx$ 0.736

SPSS Correlation Coefficient : 
![[Screenshot 2025-01-29 at 2.40.29 PM.png|500]]

Calculated Regression Line Coefficients :
b(constant) = 11.2118834
m = 143.73228226

SPSS Regression Line Coefficients : 
![[Screenshot 2025-01-29 at 2.33.42 PM.png|500]]

NOTE : Assumption that variation in values is due to rounding error during calculations when comparing calculated values to SPSS values.

<div style='page-break-after: always;'></div>

2.

a)
Given probabilities :
$$\displaylines{P(A) = 0.8 \\
P(B)= 0.25 \\
P(A\cap B) = 0.15 }$$

b)
Probability that the customer orders at least one of the two items.
We find the union of the two sets and subtract the intersection so as to not double count.
$$\displaylines{P(A\cup B) = P(A) + P(B) - P(A\cap B)\\ \\
P(A\cup B) = 0.8 + 0.25 - 0.15 = 0.9}$$


c)
Probability that the customer orders neither of the two items.
We find the complement of the union of the two sets to get the probability of choose anything except for the two items.
$$P(A\cup B)^c = 1 - P(A\cup B) = 1 - 0.9 = 0.1$$


d)
Probability that the customer orders exactly one of the two items.
We find the probability of the item from $A$ but not $B$.
We find the probability of the item from $B$ but not $A$.
We sum the two probabilities together to find the total probability that we will only have one item or the other.
$$\displaylines{P(A\cap B^c) = P(A) - P(A\cap B) = 0.8 - 0.15 = 0.65 \\
P(A^c \cap B) = P(B)-P(A\cap B) = 0.25 - 0.15 = 0.1 \\ \\
∴P(A\bigtriangleup B) = P(A\cap B^c ) + P(A^c\cap B) = 0.65 + 0.1 = 0.75}$$

<div style='page-break-after: always;'></div>



3.

a) Number of possible dice rolls from 5 dice :
	$6 \times 6 \times 6 \times 6 \times 6 = 6^5 = 7776$

b) Probability of rolling a Yahtzee, where we have six possible solutions over the total number of solutions :
	$\frac{6}{6^5} = \frac{1}{1296}$


<div style='page-break-after: always;'></div>


4.

a) 
$P(D)$ -  Probability of taking 5 or more drugs per day.
$P(D \cap M)$ - Probability of taking 5 or more drugs and being male.
$P(D\cap M^c)$ - Probability of taking 5 or more drugs and being female.

$$\displaylines{
\text{Using the Law of Total Probability :} \\
P(D) = P(D\cap M) + P(D \cap M^c) \\ 
P(D \cap M) = P(M)P(D|M) \\
P(D\cap M^c) = P(M^c)P(D|M^c) \\ \\
\text{Calculations : } \\ 
P(D\cap M) = 0.52 \times 0.22 = 0.1144 \\
P(D\cap M^c) = 0.48 \times 0.28 = 0.1344 \\
P(D) = 0.1144 + 0.1344 = 0.2488
}$$
∴ The probability that a randomly selected senior is taking 5 or more drugs per day is 24.88%.


b) 
Finding the probability of a selected person who is taking 5 or more drugs per day and being female, we can take the probability of the intersection of those two sets divided by the total probability of a senior taking 5 or more drugs. 

$$\displaylines{\text{Using Baye's Rule :} \\
P(M^c|D) = \frac{P(D\cap M^c)}{P(D)} \\ \\
\text{Calculations :} \\
P(M^c|D) = \frac{0.1344}{0.2488}\approx  0.5402}$$

∴ The probability of a person taking 5 or more drugs and being female is 54.02%.
