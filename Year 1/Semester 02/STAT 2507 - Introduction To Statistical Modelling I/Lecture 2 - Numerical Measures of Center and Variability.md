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


---
##### Numerical Measures of Relative Standing

**Percentiles**
The $p^{th}$ percentile of a data set is the value such that $p\%$ of measurements in the data set fall below this value.

Steps to find the $p^{th}$ percentile of a data set :
1. Arrange data set in ascending order.
2. Compute the position of the $p^{th}$ percentile as $\frac{P}{100}(n+1)$, where,
	P : Percentile
	n : Total number of data points in the set
3. If the position results in a decimal value, you can compute the data point through linear interpolation. $$\displaylines{x_{i} + (decimal\; \times (x_{i+1} - x_{i}) )}$$

**Quartiles**
Quartiles are special percentiles that divide the data set into quarters.

1. The first quartile, or $Q_{1}$, is the $25^{th}$ percentile.
2. The second quartile, or $Q_{2}$(**median**), is the $50^{th}$ percentile.
3. The third quartile, or $Q_{3}$, is the $75^{th}$ percentile.

The first and third quartiles frames the middle 50% of a data set. The difference between them, called the **interquartile range**, or **IQR**, is a measure of the spread of the middle 50% of data.

**Example:**
Find **Quartiles** and **IQR** for the given set.
Data set : {20, 27, 29, 31, 32, 33, 35, 39, 53}

Position of $Q_{1}$ = $\frac{25}{100} \times (9 + 1) = 2.5$
$Q_{1} = 27 + (0.5 \times (31 - 27)) = 28$

Position of $Q_{3} = \frac{75}{100} \times (9 + 1) = 7.5$
$Q_3 = 35 + (0.5 \times (39 - 35)) = 37$

∴ $IQR = 37 - 28 = 9$


---
##### The Five Number Summary

Min : The minimum observation
$Q_{1}$ : The first quartile
m : The median
$Q_{3}$ : The third quartile
Max : The maximum observation


**Selecting The Best Numerical Summary**
Bell shaped or Symmetric distribution :
	The mean and the standard deviation provide the best summary.

Skewed distribution :
	The five number summary is a better choice. We can represent the five number summary in a graph called a box plot which provides us with means to find outliers.


---
##### Box Plot
A graphical representation of quartile data.
The box is centred around the median with the borders being $Q_{1}$ and $Q_{2}$. 
The **fences**, which represent the limits of the data points before they are classified as outliers, are calculated by finding $1.5 \times IQR$ and subtracting from $Q_{1}$ to find the lower fence and adding to $Q_{3}$ to find the upper fence .
The **whiskers**, which extend from either edge of the box, are lines that extend to the upper and low values within our data set before they pass the fence.

![[Pasted image 20250114100457.png]]





