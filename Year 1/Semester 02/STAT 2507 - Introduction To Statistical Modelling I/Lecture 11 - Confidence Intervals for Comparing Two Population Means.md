(Section 8.5)


---
#### Comparing Two Population Means $\mu_{1}$ and $\mu_{2}$

The statistical inference we conduct for $\mu_{1} - \mu_{2}$ will depend on our knowledge of the population standard deviations and the sample sizes. In all cases we are selecting independent random samples from normally distributed populations.

**Case 1: $\sigma_{1}$ and $\sigma_{2}$ are known**

If we take independent random samples from each of two normally distributed populations, then a confidence interval for $\mu_{1} - \mu_{2}$ is given by : $$(\bar{X}_{1} - \bar{X}_{2}) \pm Z_{\frac{\alpha}{2}} \sqrt{ \frac{\sigma^2_{1}}{n_{1}} + \frac{\sigma^2_{2}}{n_{2}} }$$
**Note :** If the populations of measurements are not normally distributed but $n_{1}$ and $n_{2}$ are both at least 30, then this confidence interval will yield an approximately valid result.


**Example :**
Students who took an introductory statistics course can be divided into two groups: those who attended class regularly and those who did not.  

Independent random samples of 20 students were taken from each group, and their midterm exam score was recorded.  The average grades for the regular attendees and the absent students were 70.5% and 61.8%, respectively.  

Assume that the population standard deviation for both groups is 12% and the grades followed a normal distribution.  

Compute and interpret a 90% confidence interval for the mean difference in midterm exam grades.
$$\displaylines{n = 20 \\ \bar{X_{1}} = 0.705, \; \bar{X_{2}} = 0.618 \\
\sigma = 0.12 \\ \\
=(70.5 - 61.8) \pm 1.645 \times  \sqrt{ \frac{12^2}{20} + \frac{12^2}{20}} \\
= 8.7 \pm 6.2}$$
We are 90% confident that the mean difference in midterm exam grades is between 2.5 and 14.9 percentage points. That is, the students who attended class maintained a range of 2.5 - 14.9 percentage points higher than the absent students.



---
#### Case 2 vs Case 3

Case 2 : $\sigma_{1}$ and $\sigma_{2}$ are unknown, $\sigma_{1} \ne \sigma_{2}$   
Case 3 : $\sigma_{1}$ and $\sigma_{2}$ are unknown, $\sigma_{1} = \sigma_{2}$

