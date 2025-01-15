STAT 2507 E
Matthew Arsenault
101288386

1. Data Set : {16, 17, 19, 23, 24, 24, 26, 27, 31, 32, 33, 38, 40, 45, 52, 54, 67, 75, 81}

a) 
**Population :** All days in the Fall 2024 semester
**Variable :** Number of emails received on a given day
**Experimental Unit :** A single day

b) The variable is a **Discrete Quantitative Variable** as it is a finite set of integer values.

c)
1 | 679
2 | 34467
3 | 1238
4 | 05
5 | 24
6 | 7
7 | 5
8 | 1

d) Using the formula : $\text{Index} = \frac{P}{100} \times (n + 1)$ 
$$\displaylines{\frac{83}{100} \times (19 + 1) = 16.6 \\ \\
\text{Given a decimal value, we can now find the interpolated data point. }\\ \\
\text{Linear Interpolation} : 54 + (0.6 \times (67 - 54)) = 61.8\\ \\
∴ 61.8\; \text{is our data point at the 83rd percentile.}}$$

<div style="page-break-after: always;"></div>

e) $Q_{1} = 24,\; \text{Median} = 32,\; Q_{3} = 52$
Position of $Q_{3} = 0.75 * (19 + 1) = 15$
$Q_{3} = 52$
$IQR = 52 - 24 = 28$
$1.5 \times IQR = 42$

Lower Fence : $24 - 42 = -18$
Upper Fence : $52 + 42 = 94$

∴ There are no outliers within this data set as all data points are within the range of the upper and lower fences.


![[boxplot.drawio(4).png]]f) ![[Pasted image 20250114111140.png]]

g) Tchebysheff's Theorem would be more appropriate for the graph due to it being skewed to the right. 

h)$$\displaylines{\text{Mean} \\ \frac{724}{19} = 38.1 \\ \\ \\
\text{Standard Deviation} \\
\text{Combining the sample variance formula : } s^2 = \frac{\sum^{n}_{i=1}X^2_{i}-\left[ \left( {\sum^{n}_{i=1}}X_{i} \right)^2 \;/\; n \right]}{n-1} \\ \text{and the given sum values : }\sum^{19}_{i=1}x_{i} = 724,\; \sum^{19}_{i=1}x_{i}^2 = 34430 \\ \\
\sqrt{ \frac{34430 - \left( \frac{724^2}{19} \right)}{19-1} }\\ \\
\sqrt{ \frac{34430 - 27588.21}{18} }\\ \\
\sqrt{ \frac{6841.79}{18} }\\ \\
\sqrt{ 380.1 } \approx 19.5 }$$

<div style="page-break-after: always;"></div>


2. 
a) A letter grade is a string type variable.

b)![[Screenshot 2025-01-14 at 11.58.45 AM.png]]
![[Screenshot 2025-01-14 at 12.01.52 PM.png]]


c) The failing grade, **F**, could be a wide range of different percentage values. Specifically, it could be anywhere within 0% - 49%, where all the other letter grades have a much smaller range, 10% - 20%, depending on the country or school.