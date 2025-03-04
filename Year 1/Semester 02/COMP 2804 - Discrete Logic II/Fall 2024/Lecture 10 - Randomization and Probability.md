Sample Space : Non-empty countable set S
	Elements of S are called outcomes
	Subsets of S are called events

Probability Function on S : 
	$Pr : S \rightarrow [0, 1]$ such that $\sum_{w \in S} Pr(w) = 1$

Probability Space :
	$(S, Pr)$, where $S$ is the sample space and $Pr$ is a probability function on $S$.


Example : Toss a coin
$$\displaylines{S = \{H, T\} \\
Pr(H) = Pr(T) = 0.5}$$


Example : Toss two coins
$$\displaylines{S = \{HH,HT, TH, TT\} \\
Pr(HH) = Pr(HT) = Pr(TH) = Pr(TT) = 0.25}$$


Example : Roll a six-sided die
$$\displaylines{S=\{1, 2, 3, 4, 5, 6\} \\
Pr(1) = Pr(2) = Pr(3) = Pr(4) = Pr(5) = Pr(6) = \frac{1}{6}}$$


Example : Roll two die. One red and one blue.
$$\displaylines{S = S^2 = \{(i, j): i,j \; \in \{1, 2, 3, 4, 5, 6\}\} \\
|S| = 36, \;Pr(i,j) = \frac{1}{36} \text{ for each } i,j \; \in \{1, \dots, 6\}}$$

For any integer $k \in \{1, \dots, 12\}$, define the event.
	$A_{k} =$ "The sum of the two dice is equal to $k$"
	$A_4 = \{(1, 3), (2, 2), (3, 1)\}$
	$Pr(A_{4}) = Pr(1, 3) + Pr(2, 2) + Pr(3, 1) = \frac{1}{36} + \frac{1}{36} + \frac{1}{36} = \frac{3}{36} = \frac{1}{12}$

