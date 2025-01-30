##### Bivariate Data
**Bivariate data** are obtained when two variables are measured on each experimental unit.
When dealing with bivariate data, we usually want to investigate the relationship between the two variables.

Two **Qualitative** Variables : 
	Side-by-side pie charts
	Bar charts in which the bars for the two groups are adjacent
	A stacked bar chart where the data is stacked on top of each other

Ex. 
	Persons smoking status and education level.

One **Qualitative** Variable and One **Quantitative** Variable:
	Bar charts in which the bars for the two groups are adjacent

Ex.
	A student's major and GPA.
	
Two **Quantitative** Variables:
	A Scatterplot with x and y beings the two quantitative variables

Ex. 
	A person's height and weight.



---
##### Numerical Measure for Quantitative Bivariate Data

**The Dependent Variable and Independent Variable**
Dependent Variable :
	The variable who's values we want to predict and is denoted as $Y$.

Independent Variable : 
	The variable on which we base our predictions and is denoted as $X$.


**Population Covariance**
The population covariance between two variables, $X$ and $Y$, denoted by $\sigma_{xy}$, is a measure of the linear dependence between $X$ and $Y$.

Positive Covariance : 
	As one variable changes, the other tends to move in the same direction.

Negative Covariance : 
	As one variable changes, the other tends to move in the opposite direction.


**Sample Covariance**
Take a random sample of $n$ pairs of values :
	$(x_{1}, y_{1}), (x_{2}, y_{2}),\dots,(x_{n}, y_{n})$

Formula for **Sample Covariance** : 
$$s_{xy} =\frac{\sum^{n}_{i=1}X_{i}Y_{i}-\frac{\left( \sum^{n}_{i=1}X_{i} \right)\left( \sum^{n}_{i=1}Y_{i} \right)}{n}}{n-1}$$

Example :

| Beers | BAC   | Beers | BAC   |
| ----- | ----- | ----- | ----- |
| 5     | 0.100 | 3     | 0.020 |
| 2     | 0.030 | 5     | 0.050 |
| 9     | 0.190 | 4     | 0.070 |
| 8     | 0.120 | 6     | 0.100 |
| 3     | 0.040 | 5     | 0.085 |
| 7     | 0.095 | 7     | 0.090 |
| 3     | 0.070 | 1     | 0.010 |
| 5     | 0.060 | 4     | 0.050 |
y = BAC (Dependent Variable)
x = # of Beers (Independent Variable)

$\sum^{16}_{i=1}Y_{i} = 1.18$
$\sum^{16}_{i=1}X_{i} = 77$
$\sum^{16}_{i=1}X_{i}Y_{i} = 6.98$
$\sum^{16}_{i=1}X^2_{i} = 443$
$\sum^{16}_{i=1}Y^2_{i} = 0.11625$

$$S_{xy} = \frac{6.98 - \frac{(77)(1.18)}{16}}{16-1} = \frac{1.30125}{15} = 0.08675$$


---
##### Population Correlation Coefficient
The correlation coefficient is a unitless measure of the direction and strength of the linear dependence between $X$ and $Y$. Denoted as $\rho$.

Formula : $$\rho = \frac{\sigma_{xy}}{\sigma_{x}\sigma_{y} }$$
The population correlation coefficient is always a value between -1 and 1, inclusive.
If the value results in 0, then there is no linear relationship between the variables.
$$\displaylines{-1\leftarrow\; 0\; \rightarrow 1 \\
\;\;\vdash --\mid-- \dashv\\}$$


Sample Correlation Coefficient Formula : $$r = \frac{s_{xy}}{s_{x}s_{y}}$$
$s_{xy}$ - Sample Covariance
$s_{x}$ - Std. Deviation of x
$s_{y}$ - Std. Deviation of y



---
##### The Least-Squares Regression Line

If $X$ and $Y$ appear to have an approximate linear relationship, then we can approximate the relationship using the equation of a line : $$Y = mX + b$$
where $$\displaylines{b - \text{y-intercept} \\ m - \text{slope}}$$
The best fitting line relating $Y$ to $X$ is called the **least-squares regression line**.
The least-squares regression line is found by minimizing the sum of the squared vertical differences between the data points and the line.

The least-squared regression line is $Y = mX + b$ where, $$\displaylines{m = r\frac{s_{y}}{s_{x}}\\\; b = \overline{y} - m\overline{x} \\ \\
\overline{x} - \text{ The mean of all x-values}\\
\overline{y} - \text{ The mean of all y-values}}$$
Example : 

| Beers | BAC   | Beers | BAC   |
| ----- | ----- | ----- | ----- |
| 5     | 0.100 | 3     | 0.020 |
| 2     | 0.030 | 5     | 0.050 |
| 9     | 0.190 | 4     | 0.070 |
| 8     | 0.120 | 6     | 0.100 |
| 3     | 0.040 | 5     | 0.085 |
| 7     | 0.095 | 7     | 0.090 |
| 3     | 0.070 | 1     | 0.010 |
| 5     | 0.060 | 4     | 0.050 |
$$\displaylines{m = r\frac{s_{y}}{s_{x}} = \frac{s_{xy}}{s_{x}s_{y}}\frac{s_{y}}{s_{x}}= \frac{s_{xy}}{s^2_{x}} = \frac{0.08675}{4.82916} \approx 0.017964 \\ \\
b = \overline{y} - m\overline{x} \approx \frac{1.18}{16} - 0.017964 \times \frac{77}{16} \approx -0.01270 \\ \\
∴ y = 0.017964x - 0.01270 \\ \\
x = 5 \\
y = 0.017964\times 5 - 0.01270 \approx 0.077 \frac{g}{100mL}}$$


