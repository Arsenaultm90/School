STAT 2507 E
Matthew Arsenault
101288386

1.
a)$$\displaylines{X \sim \exp(\mu) \\ P(X > x) = e^{-a/\mu} \\ \\ \mu = 4 \\ P(X > 3) = e^{-3/4} = 0.4724  \\ \\
∴ \text{ The probability that a machine operates for more than 3 days is 47.24\%}}$$
b)$$\displaylines{P(2.5 \leq x \leq 6) = P(X \leq 6) - P(X \leq 2.5) \\
P(X \leq 2.5) =1- e^{-2/4} = 0.4647\\
P(X \leq 6) = 1 - P(X > 6) = 1 - e^{-6/4} = 0.7769 \\ \\
P(2.5 \leq x \leq 6) = 0.7769 - 0.4647 = 0.3122 \\ \\
∴ \text{ The probability that a machine operates for at least 2 days but no more than 6 is 31.22\%}}$$

c)
![[Screenshot 2025-03-16 at 11.10.04 AM.png|500]]

We notice that while it still contains a right-skewed distribution, it starts to slightly approach a **Normal Distribution**. Only a slight change occurs due to small 'n'.

d)
![[Screenshot 2025-03-16 at 11.16.03 AM.png|500]]

We can see that with a sample size of 5000, and 100 failures per sample, the histogram displays a **Normal Distribution**. As expected due to the **Central Limit Theorem**.

e) We can see the biggest change in the deviation, where the sample with 100 failures has a significantly smaller deviation compared to 2 failures. This makes sense as averaging reduces variability in sample means.


2.
a) $$\displaylines{\text{Binomial Distribution : } \\ X \sim Binomial(n,p) \\ \\
n = 196 \\
p=0.2 \\
q = 1-p = 0.8 \\ \\
\text{Parameters :} \\
\mu_{x} = np = 196 \times 0.2 = 39.2 \\
\sigma_{x} = \sqrt{ npq } = \sqrt{ 196 \times 0.2 \times 0.8 } \approx 5.6 }$$

b) To find the approximation of '**X**', we can use the **Normal Approximation To The Binomial Distribution**.

Check that it fits the requirements of rule of thumb : $$\displaylines{np \geq 5 \text{ and } n(1-p) \geq 5 \\
np = 196 \times 0.2 = 39.2 \\
n(1-p) = 156.8}$$
c) Find Z-Score : $$\displaylines{P(X \geq 50) \\ \\
\text{ Continuity Correction : } \\ P(X \geq 49.5) \\ \\
\text{Convert to Z-Domain : }\\
P=(Z \geq \frac{49.5 - 39.2}{\sqrt{ 196 \times 0.2(1-0.2) }}) = P(Z \geq 1.84) \\ \\
\text{ Use lookup table :} \\
P(Z \geq 1.84) = 1 - P(Z < 1.84) = 1 -0.9671 = 0.0329}$$
∴ There is a 3.29% chance that at least 50 homeowners, within the sample, have a mortgage. 

<div style='page-break-after: always;'></div>

3.
a)$$\displaylines{P(X \geq 1500) \\
Z = \frac{1500-1350}{100} = 1.5 \\ \\
P(Z \geq 1.5) = 1 - P(Z < 1.5) = 1 - 0.9332 = 0.0668}$$
∴ There is a 6.68% probability that a brain weighs 1500g or more.


b) Using Central Limit Theorem : $$\displaylines{\mu_{\overline{X}} = \mu = 1350 \\
\sigma_{\overline{X}} = \frac{\sigma}{\sqrt{ n }} = \frac{100}{\sqrt{ 25 }} = 20}$$
We can see the standard deviation of the sample distribution is smaller than the population standard deviation. This makes sense since the 'standard error' decreases when we average the data points. This would lead us to a normal distribution. $$X \sim N(1350, 20)$$

c)
$$\displaylines{P(1310 \leq X \leq 1340) \\
P(1310 \leq X) = P(\frac{1310-1350}{20} \leq Z) = P(-2 \leq Z) \\
P(Z \leq 1340) = P(Z \leq \frac{1340-1350}{20}) = P(Z \leq -0.5) \\ \\
P(-2 \leq Z \leq -0.5) = P(Z < -0.5) - P(Z < -2) \\
=0.3085 - 0.0228 \\
= 0.2857}$$
∴ There is a 28.57% chance that the average weight falls between 1310g and 1340g.


d)$$\displaylines{P(X > x) = 0.6 \\
Z = -0.25 \\ \\ 
Z = \frac{x-\mu}{\sigma} \implies -0.25 = \frac{x-1350}{100} \\
x = (-0.25 \times 100) + 1350 \\
=1325g}$$
∴ 60% of the population's brains weigh more than 1325g.


