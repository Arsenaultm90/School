Matthew Arsenault
101288386

1. (4 points) Let’s build a random undirected graph G = (V, E) over |V | = n so that an edge between any two nodes u ̸= v ∈ V appears with probability 1/4. Denote the number of edges in the resulting graph A = |E| and notice that it is a random variable. Calculate the expected value E [A]

The total possible edges in the graph is given by the binomial coefficient : $$\binom{n}{2} = \frac{n(n-1)}{2}$$
We then have the indicator variable : $$X_{e}=\left\{\begin{array}{rlc}
1 & \text{if the edge e exists in G}  \\
0 & \text{otherwise}
\end{array} \right.$$
Expected value of $X_{e}$ : $$E(X_{e}) = 1 \times \frac{1}{4} + 0 \times \left( 1 - \frac{1}{4} \right) = \frac{1}{4}$$
By Linearity of Expectation : $$\displaylines{E(A) = E\left( \sum_{e}X_{e} \right) = \sum_{e}E(X_{e}) \\ \\
 ∴ E(A) = \binom{n}{2}· \frac{1}{4} \\= \boxed{\frac{n(n-1)}{8}}}$$
<div style='page-break-after: always;'></div>

2. (4 points) Given a random variable X with the values and their probabilities given in the following table.

| Value       | 1   | -1  | 2   | -3  | 3   |
| ----------- | --- | --- | --- | --- | --- |
| Probability | 1/4 | 1/4 | 1/6 | 1/6 | 1/6 |



Calculate the exact values (meaning single numbers) of:

(a) E[X]  $$\displaylines{= \left( 1 \times \frac{1}{4} \right) + \left( -1 \times \frac{1}{4} \right) + \left( 2 \times \frac{1}{6} \right) + \left( -3 \times \frac{1}{6} \right) + \left( 3 \times \frac{1}{6} \right) \\
= \frac{1}{3}}$$
(b) Var[X] $$\displaylines{ = E(X^2) - [E(X)]^2   \\ \\
E(X^2) = \sum x^2P(X=x) \\
= \left( 1^2 \times \frac{1}{4} \right) + \left( -1^2 \times \frac{1}{4} \right) + \left( 2^2 \times \frac{1}{6} \right) + \left( -3^2 \times \frac{1}{6} \right) + \left( 3^2 \times \frac{1}{6} \right) \\
=\frac{1}{4} + \frac{1}{4} + \frac{2}{3} + \frac{3}{2} + \frac{3}{2} \\
= \frac{25}{6} \\ \\
[E(X)]^2 = \left( \frac{1}{3} \right)^2 \\
= \frac{1}{9} \\ \\
V(X) = \frac{25}{6} - \frac{1}{9} = \frac{75}{18} - \frac{2}{18} \\
= \frac{73}{18}}$$
(c) σ[X] $$\displaylines{ = \sqrt{ \frac{73}{18}} \\
= 2.014}$$
<div style='page-break-after: always;'></div>



3.  (4 points) Alice and Bob are playing with a tailored (biased) die. Both the probability of the die showing 2 and the probability of it showing 4 are equal to 1/3. All other values of the die can appear with equal probability to each other as well (though, obviously, not 1/3). Alice wins a die toss if an even number appears. Otherwise, Bob wins the toss. Denote by X the number of times Alice wins out of 10 sequential tosses of the die. Calculate the exact value (down to a single number, please) of:
$$\displaylines{P(1) + P(2) + P(3) + P(4) + P(5) + P(6) = 1 \\ \\
P(1) = P(3) = P(5) = P(6) = p \\
 \frac{1}{3} + \frac{1}{3} + 4p = 1 \\
p = \frac{1}{12} \\
P(A) = \frac{1}{3} + \frac{1}{3} + \frac{1}{12} = \frac{9}{12} = \frac{3}{4}}$$

(a) E[X] $$\displaylines{\text{Binomial Random Variable} \\ X \sim B\left( 10, \frac{3}{4} \right) \\
E(X) = np = 10\times \frac{3}{4} \\
= \frac{30}{4} = \frac{15}{2} = \boxed{7.5}}$$
(b) Var[X] $$\displaylines{= np(1-p) \\
=10 \times \frac{3}{4}\left( 1- \frac{3}{4} \right) \\
= \frac{30}{16} = \boxed{\frac{15}{8}}}$$

<div style='page-break-after: always;'></div>

4. (4 points) A pink handbag will have a print of green flowers with probability 1/3, and a print of violet flowers with probability 2/3. On the other hand, a yellow handbag will have a green flower print with probability 1/4 and an aquamarine flower print with probability 3/4. Assuming that pink and yellow handbags are bought with equal probability, calculate the exact probability (once more single number, please) that a handbag with a print of green flowers is being bought.

Using the law of total probability : $$\displaylines{P(Green) = P(Green | Pink)P(Pink) + P(Gre en | Yel low)P(Yel low) \\
= \left( \frac{1}{2} \times \frac{1}{3} \right) + \left( \frac{1}{2} \times \frac{1}{4} \right) \\
= \frac{1}{6} + \frac{1}{8} \\
=\frac{7}{24}}$$

<div style='page-break-after: always;'></div>

5. (4 points) Alice and Bob are playing a game by taking turns in tossing a coin. When the coin shows "heads", the game stops, and the player who tossed it wins. Alice starts, and the coin has the probability of "heads" equal to 3/4. Calculate exact probabilities, down to a single number, that
    
a) Alice wins the game $$\displaylines{\text{Probability Alice wins first toss :} \frac{3}{4} \\
\text{Probability Alice wins on second toss :} \frac{1}{4} \times \frac{1}{4} \times \frac{3}{4} \\
\text{Probability Alice wins her third toss : } \left( \frac{1}{4} \times \frac{1}{4} \right)^2 \times \frac{3}{4}}$$
We arrived at an infinite geometric series in the form of : $\sum^\infty _{x=0} x^i = \frac{1}{1-x}$
$$\displaylines{∴ P(A) = \frac{3}{4} \times \frac{1}{1- \frac{1}{16}} \\
=\frac{3}{4} \times \frac{16}{15} \\
= \boxed{\frac{4}{5}}}$$

b) Bob wins the game
$$\displaylines{\text{Probability Bob wins on his first toss : } \frac{1}{4} \times \frac{3}{4} \\
\text{Probability Bob wins on his second toss : } \left( \frac{1}{4} \times \frac{1}{4} \right) \times \frac{1}{4} \times \frac{3}{4}}$$

Since we will once again find it in the form of an infinite geometric series we can apply the same methods used above. 
$$\displaylines{P(B) = \frac{3}{16} \times \frac{1}{1- \frac{1}{16}} \\
= \frac{3}{16} \times \frac{16}{15} \\
= \boxed{\frac{1}{5}}}$$

