(Section 8.5)


---
#### Comparing Two Population Means $\mu_{1}$ and $\mu_{2}$

The statistical inference we conduct for $\mu_{1} - \mu_{2}$ will depend on our knowledge of the population standard deviations and the sample sizes. In all cases we are selecting independent random samples from normally distributed populations.


---
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
#### Case 2

Case 2 : $\sigma_{1}$ and $\sigma_{2}$ are unknown, $\sigma_{1} \ne \sigma_{2}$   

When taking independent random samples from each of two normally distribution populations where $\sigma_{1}$ and $\sigma_{2}$ are unknown and unequal, $$T = \frac{(\overline{X}_{1}-\overline{X}_{2})-(\mu_{1}-\mu_{2})}{\sqrt{ \frac{s^2_{1}}{n_{1}}+\frac{s^2_{2}}{n_{2}} }} \sim t_{df}$$
where, $$df = \frac{\left( \frac{s^2_{1}}{n_{1}}+ \frac{s^2_{2}}{n_{2}} \right)^2}{\frac{\left( \frac{s^2_{1}}{n_{1}} \right)^2}{(n_{1}-1)}+\frac{\left( \frac{s^2_{2}}{n_{2}} \right)^2}{(n_{2}-1)}}$$
But that is a lot of work for an estimation so we can get a conservative estimation using : $$df = min(n_{1}-1, n_{2}-1)$$

If we take independent random samples from each of two normally distributed populations, then a $(1 - \alpha)100\%$ confidence interval for $\mu_{1}-\mu_{2}$ is given by : $$(\bar{X}_{1}- \bar{X}_{2}) \pm t_{\frac{\alpha}{2},df} \sqrt{ \frac{s^2_{1}}{n_{1}}+ \frac{s^2_{2}}{n_{2}} }$$



**Example :** 
Your professor likes to order food delivery from two restaurants. For two independent samples of deliveries, he records the delivery time, in minutes.  

The summary sample statistics are provided below.

|                    | Restaurant 1 | Restaurant 2 |
| ------------------ | ------------ | ------------ |
| Mean               | 32.4         | 46.2         |
| Standard Deviation | 3.2          | 6.1          |
| Sample Size        | 16           | 12           |
Compute and interpret a 99% confidence interval for the true mean  
difference in delivery times.

Check rule of thumb : $$\frac{s^2_{1}}{s^2_{2}} = \frac{3.2^2}{6.1^2} \approx 0.28 \not\in \left[ \frac{1}{3},\; 3 \right]$$
∴ Assume $\sigma_{1} \ne \sigma_{2}$

For a 99% confidence internal, $$\displaylines{\alpha = 0.01 \rightarrow \frac{\alpha}{2} = 0.005 \\
df = min(n_{1}-1, n_{2}-1) = min(16-1, 12-1) = 11 \\
t_{0.005, 11} = 3.106}$$

We can now plug everything into our confidence interval formula, $$\displaylines{(32.4 - 46.2) \pm 3.106\sqrt{ \frac{3.2^2}{16}+ \frac{6.1^2}{12} } \\
= -13.8 \pm 6.0 \text{ or } (-19.8, -7.8)}$$
∴ We are 99% confident that, on average, Restaurant 1  delivery times are 7.8 to 19.8 minutes lower than Restaurant 2 delivery times.



**Rule Of Thumb :**$$\frac{1}{3} \le \frac{s^2_{1}}{s^2_{2}} \le 3, \text{ it is reasonable to assume } \sigma_{1} = \sigma_{2}$$

---
#### Case 3 

Case 3 : $\sigma_{1}$ and $\sigma_{2}$ are unknown, $\sigma_{1} = \sigma_{2}$

Pooled Sample Variance : $$s^2_{p} = \frac{(n_{1}-1)s^2_{1}+(n_{2}-1)s^2_{2}}{n_{1}+n_{2}-2}$$

If we take independent random samples from each of two normally distributed populations, then a $(1 - \alpha)100\%$ confidence interval for $\mu_{1}-\mu_{2}$ is given by :  $$(\bar{X}_{1}- \bar{X}_{2}) \pm t_{\frac{\alpha}{2}, n_{1}+n_{2}-2} \sqrt{ s^2_{p}\left( \frac{1}{n_{1}}+ \frac{1}{n_{2}} \right) }$$
$$df = n_{1} + n_{2} - 2$$


**Example :**
A random sample of 15 Canadian males produced an average height of 176.8 cm and a standard deviation of 6.5 cm.  

A random sample of 15 Canadian females produced an average height of 160.5 cm and a standard deviation of 6.1 cm.  

Assuming the heights of both sexes follow a normal distribution, compute and interpret a 90% confidence interval for the difference in the average height between Canadian males and females.

$$\displaylines{n_{1} = 15 \\
\bar{X}_{1} = 176.8 \\
\sigma_{1} = 6.5 \\ \\
n_{2} = 15 \\
\bar{X}_{2} = 160.5 \\
\sigma_{2} = 6.1}$$

Let's find the $\alpha$ and degrees of freedom for our $t$ value. $$\displaylines{\alpha = 1-0.9 = 0.1 \\
df = n_{1} + n_{2}-2 = 15 + 15 -2 = 28 \\
t_{\frac{\alpha}{2}, df} = t_{0.05, 28} = 1.701}$$
Now we need our pooled sample variance. $$\displaylines{s^2_{p} = \frac{(15-1)^26.5^2 + (15-1)^26.1^2}{15+15-2} = 39.73}$$
We now have all variables required to fill in our formula for the confidence interval. $$\displaylines{=(176.8-160.5) \pm 1.701\sqrt{ 39.73\left( \frac{1}{15}+\frac{1}{15} \right) } \\
=16.3 \pm 3.9 \text{ or } (12.4, 20.2)}$$

∴ We are 90% confident that, on average, Canadian males are 12.4cm to 20.2cm taller than Canadian females. 

These results are valid because we have :
1. Independent Random Samples
2. The variable we are measuring is normally distributed




---
#### A Confidence Interval For Comparing Two Population Proportions

**Notation :** $$\displaylines{\text{Population Proportion - } p_{1} \\
\text{Sample Proportion - } \hat{p}_{1} = \frac{x_{i}}{n_{i}}}$$
where $x_i$ is the number of successes out of $n_{i}$ trials. 



**Point Estimator of $p_{1} - p_{2}$**
We can estimate $p_{1} - p_{2}$ with the point estimator, $\hat{P}_{1} - \hat{P}_{2}$.

If $n_{1}p_{1}, n_{1}q_{1}, n_{2}p_{2}, n_{2}q_{2}$ are all at least 5, then $$\displaylines{\hat{P}_{1}- \hat{P}_{2} \sim N\left( p_{1}-p_{2}, \frac{p_{1}q_{1}}{n_{1}} + \frac{p_{2}q_{2}}{n_{2}} \right) \rightarrow \frac{(\hat{P}_{1}- \hat{P}_{2})- (p_{1}-p_{2})}{\sqrt{ \frac{p_{1}q_{1}}{n_{1}}+ \frac{p_{2}q_{2}}{n_{2}} }} \sim N(0, 1)}$$

**A Confidence Interval For $p_{1} - p_{2}$**
Taking independent random samples from each of two populations, a $(1-\alpha)100\%$ confidence interval for $p_{1}- p_{2}$ is given by: $$(\hat{p}_{1}- \hat{p}_{2}) \pm Z_{\frac{\alpha}{2} }\sqrt{ \frac{\hat{p}_{1}\hat{q}_{1}}{n_{1}}+ \frac{\hat{p}_{2}\hat{q}_{2}}{n_{2}} }$$
This confidence interval will produce approximately valid results provided there are at least 5 “successes” and 5 “failures” in each sample.


**Example :** 
In a study of the relationship between birth order and university success, a random sample of  
180 university graduates produced 126 people who were firstborn children. In a random sample  
of 100 non-graduates of comparable age and socio-economic background, there were 54  
firstborn children.  

Estimate the difference in firstborn children between these two groups with 90% confidence. Interpret your results. $$\displaylines{\hat{p}_{1} = \frac{126}{180} = 0.7\\
\hat{p}_{2} = \frac{54}{100} = 0.54 \\ 
\alpha = 1-0.9 = 0.1\\ \\
(\hat{p}_{1}- \hat{p}_{2}) \pm Z_{\frac{\alpha}{2} }\sqrt{ \frac{\hat{p}_{1}\hat{q}_{1}}{n_{1}}+ \frac{\hat{p}_{2}\hat{q}_{2}}{n_{2}} } \\
= (0.7 - 0.54) \pm 1.645 \sqrt{ \frac{0.7 \times 0.3}{180} + \frac{0.54 \times 0.46}{100} } \\
= 0.16 \pm 0.0994 \text{ or } (0.0606, 0.2593)}$$
We are 90% confident that the proportion of first born children among university graduates is 0.0606 to 0.2593 higher than non-graduates. 

This results is approximately valid because :
1. We took independent random samples
2. There are at least 5 successes and 5 failures

