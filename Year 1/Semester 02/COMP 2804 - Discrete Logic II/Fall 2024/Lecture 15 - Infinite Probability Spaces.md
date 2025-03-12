$$\displaylines{\sum^\infty_{n=0} x^n = \lim_{N \to \infty }  \sum^\infty_{n=0} x^n = \lim_{ N \to \infty } \sum^\infty_{n=0} \frac{1-x^{N+1}}{1-x} = \frac{1}{1-x}, \text{ for } -1 < x <1}$$

**Law of Total Probability** : $$\displaylines{P(A) = P(B)P(A|B) + P(B)P(A|\overline{B})}$$
**Probability Space :** $$\displaylines{(S, P) \\
S - \text{ is a non-empty countable set} \\
P: S \rightarrow [0, 1] \\
\sum_{x \in S}P(x) = 1}$$

Example : 
Toss a coin repeatedly until the coin comes up heads. $$\displaylines{S = \{T^nH : n \geq 0\} \;\;\; P(T^nH) = \frac{1}{2^{n+1}} \\
\sum_{x \in S}P(x) = \sum^\infty_{n=0}P(T^nH) = \sum^\infty_{n=0} \frac{1}{2^{n+1}} = \frac{1}{2} \sum^\infty_{n=0} \frac{1}{2^n}}$$
For $x = \frac{1}{2}$, $$\displaylines{\frac{1}{1-x} = \frac{1}{1-\frac{1}{2}} = 2}$$
$$\displaylines{\frac{1}{2} \sum^\infty_{n=0} \frac{1}{2^n} = \frac{1}{2}·2 = 1}$$


Example : 
Who flips the first head?

A = "Player 1 wins the game" = {H, TTH, TTTTH, ....} : $$\{T^{2n}H : n \geq 0\}$$
$$\displaylines{P(A) = \sum_{x \in A}P(x) = \sum^\infty_{n=0}P(T^{2n}H) = \sum^\infty_{n=0} \frac{1}{2^{2n+1}} = \frac{1}{2} \sum^\infty_{n=0} \left( \frac{1}{2} \right)^{2n} = \frac{1}{2} \sum^\infty_{n=0} \left( \frac{1}{4} \right)^n \\ \\
\text{ Apply formula} \\
= \frac{1}{2} \left( \frac{1}{1-\frac{1}{4}} \right) = \frac{1}{2} \left( \frac{1}{\frac{3}{4}} \right) = \frac{1}{2}\left( \frac{4}{3} \right) = \frac{4}{6} = \frac{2}{3}}$$
$$\displaylines{∴ P(A) = \frac{2}{3} \\
P(\overline{A}) = 1-\frac{2}{3} = \frac{1}{3}}$$


Example : 
Who flips the second head?
$$\displaylines{S = \{T^nHT^mH : m,n \geq 0\}\;\;\; P(T^nHT^mH) = \frac{1}{2^{n+m+2}}}$$
Long Form - Summation
Short Form - Total law of probability
