##### Measures of Central Tendency
Two common ways to measure the 'centre' of a data set are the **mean** and **median**.

**Mean :** 
	Average of all the values.

**Median :** 
	Center value when the data points are arranged in ascending order.


---
##### Population Mean vs Sample Mean

**Population Mean**
The average of all values in an entire population of '**N**' observations.
$$\displaylines{\mu = \frac{\sum^{N}_{i = 1}X_{i}}{N} = \frac{X_{1}+X_{2}+\dots+X_{N}}{N}}$$

**Sample Mean**
The average of value from a subset(sample) of the population of '**n**' observations.
$$\displaylines{\overline{X} = \frac{\sum^{n}_{i = 1}}{n} = \frac{X_{1}+X_{2}+\dots+X_{n}}{n}}$$

**Population Parameter**
Any numerical measure computed using a population of measurements.
Ex. $\mu$

**Sample Statistic**
Any numerical measure computed from a sample of measurements.
Ex. $\overline{X}$

**Point Estimate**
A single number that estimates the value of the corresponding population parameter.
Ex. An observed value of the sample mean, $\overline{X}$, is a **point estimate** of the population mean $\mu$.


---
##### Comparing Mean and Median
If the **mean** and **median** are approximately equal, then the distribution of measurements is approximately **symmetrical**.

If the **mean** is less than the **median**, then the distribution of measurements is **skewed to the left.**

If the **mean** is greater than the **median**, then the distribution of measurements is **skewed to the right**.


---
##### Measures of Spread
Measuring the spread of the values in a distribution is the analysis of how the measurements are spread our relative to each other.

**Range**
The **range**, **R**, of a data set is the maximum observation minus the minimum observation.

**Standard Deviation**
The **standard deviation** is a measure of the amount of variation of the values about its mean. Before we can define the standard deviation, we need to define the **variance**.

The **variance** of a data set can be thought of as the average squared distance of the measurements from the mean.

**Population Variance**
$$\displaylines{\sigma^2 = \frac{\sum^{N}_{i=1}(X_{i}-\mu)^2}{N}}$$

**Sample Variance**
$$\displaylines{s^2 = \frac{\sum^{n}_{i=1}(X_{i} - \overline{X})^2}{n-1}}$$


Now we can just take the square root of a calculated variance to give us the standard deviation of a data set.
$$\displaylines{\sigma = \sqrt{\sigma^2 }\\s = \sqrt{ s^2 }}$$

**NOTE :** 
	A more computationally efficient method of calculating the sample variance is given by:
	$$\displaylines{s^2 = \frac{\sum^{n}_{i=1}X^2_{i}-[({\sum^{n}_{i=1}}X_{i})^2 \;/\; n]}{n-1}}$$

**Example:** 
Pokemon Detective Pikachu - $54 Million
John Wick: Chapter 3 - $57 Million
Rocketman - $26 Million
Once Upon A Time In Hollywood - $41 Million
Men In Black International - $30 Million

$$\displaylines{\text{Range = Max - Min}= 57 - 26 = $31\; Million\\
\sum^{n}_{i=1}X_{i} = 208\\
\sum^{n}_{i=1}X_{i}^2 = 54^2 + 57^2 + 26^2 + 41^2 + 30^2 = 9422\\
s^2 = \frac{9422 - (208^2 / 5)}{5 - 1} = \frac{769.2}{4} = 192.3 \\
∴s = \sqrt{ 192.3 } \approx $13.87\; Million}$$


**Robust Statistics**
A **Robust Statistic** is a sample statistic whose value is not easily influenced by outliers.


---
##### The Empirical Rule
Rule used to find the percentage of measurements within an interval of standard deviations. Can only be used on bell shaped distributions.

1. Approximately 68% of the measurements lie within one standard deviation of the mean.
2. Approximately 95% of the measurements lie within two standard deviations of the mean.
3. Approximately 99.6% of the measurements lie within three standard deviations of the mean.

![[Pasted image 20250112115306.png]]

**Example:**
A distribution of measurements is approximately mound shaped with a mean of 100 and a standard deviation of 10. Approximately what percentage of measurements fall between:

a) 90 and 100
	$(\mu - \sigma, \mu + \sigma) \rightarrow 68\%$

b) 80 and 120
	$(\mu - 2\sigma,\;\mu+2\sigma) \rightarrow 95\%$

c) 90 and 120
	$(\mu - \sigma,\;\mu + 2\sigma) \rightarrow 81.5\%$


---
##### Tchebysheff's Theorem

For any data set and any value $k \geq 1$, at least $100(1-\frac{1}{k^2})\%$ of all measurements will lie within $k$ standard deviations of the mean.

This tells us the minimum percentage of measurements that will fall within the interval:
$$\displaylines{\overline{X}\pm ks \; or \; \mu \pm k \sigma}$$

Example:

| <center>k</center> | **$100(1-\frac{1}{k^2})\%$** |
| ------------------ | ---------------------------- |
| <center>1</center> | 0%                           |
| <center>2</center> | 75%                          |
| <center>3</center>                  | 88.8%                        |
