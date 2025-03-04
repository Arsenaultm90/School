STAT 2507 E
Matthew Arsenault
101288386

1.
a)$$\displaylines{\text{The Hypergeometric Probability Distribution} \\
X\sim H(N,M,n) \\ \\
X \sim H(N=30, M=20, n=9) \\
\text{Total Population Size : }N = 30 \\
\text{Total Number Of Priceless Artifacts(Successes) : } M = 20 \\
\text{Number of Artifacts Stolen(Sample Size) : }n=9}$$
b)$$\displaylines{\text{Expectation Formula For Hypergeometric Distribution} \\ E[X] = t \times \frac{S}{N} \\ \\
E[X] = 9 \times \frac{20}{30} = 6}$$
c)$$\displaylines{\text{Probability Of 'k' Successes} \\ \\ P(X=k) = \frac{C^M_{k}C^{N-M}_{n-k}}{C^N_{n}} \\ \\
P(X=6) = \frac{C^{20}_{6}C^{30-20}_{9-6}}{C^{30}_{9}} \\ \\
 = \frac{C^{20}_{6}C^{10}_{3}}{C^{30}_{9}} \\ \\
 = \frac{\frac{20!}{6!(20-6)!}·\frac{10!}{3!(10-3)!}}{\frac{30!}{9!(30-9)!}} \\ \\
 = \frac{38760·120}{14307150} \\ \\
 \approx0.3251}$$
d)
![[Screenshot 2025-03-02 at 9.32.06 AM.png|150]]


e)$P(6) =$ ![[Screenshot 2025-03-02 at 9.32.55 AM.png|150]]  or 32.51%

<div style='page-break-after: always;'></div>

2.
a)
Binomial Distribution
$X \sim Binomial(n=16,\; p=0.25)$
Number of trials: n = 16
Probability of success: p = 0.25
Probability of failure: q = 1 - p = 0.75

b)
Binomial Probability Formula $$\displaylines{P(X=k) = \binom{n}{k}p^k(1-p)^{n-k} \\ \\
\binom{16}{3} = \frac{16!}{3!(16-3)!} = 560 \\
(0.25)^3 = 0.0156 \\
(0.75)^{13} = 0.0238 \\ \\
P(X=3) = 560\times 0.0156 \times 0.0238 \\
=0.2075 \text{ or } 20.75\%}$$

c)
![[Screenshot 2025-03-02 at 9.57.03 AM.png|150]]

d)
Probability at least 6 people are ineligible is 0.9204 or 92.04%

e)
$$\displaylines{P(7 \geq X \geq 9) = P(X=7) + P(X=8) + P(X=9) \\
=P(X\leq9) - P(X\leq7) \\
=0.9984 - 0.9729 \\
=0.0255 \text{ or } 2.55\%}$$

<div style='page-break-after: always;'></div>

3.
Poisson Distribution
$$\displaylines{P(X=k) = \frac{\mu^ke^{-\mu}}{k!} \\
\text{X = number of events} \\
\text{k = number of events we are interested in} \\
\mu \text{ = number of events within the given interval } \\
e \text{ = eulers number} \\ \\
\mu = \frac{8}{3} \approx 2.67 \\
P(X \geq 2) = 1 - P(X = 0) - P(X=1) \\
P(X=0) = \frac{2.67^0e^{-2.67}}{0!} = e^{-2.67} = 0.06925 \\
P(X=1) = \frac{2.67^1e^{-2.67}}{1!} = 0.1849 \\ \\
∴P(X \geq 2) = 1 - 0.06925 - 0.1849 = 0.74585 \approx 74.59\%}$$


