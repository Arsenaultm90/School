Combinatorics is the branch of math where we count the number of different, valid combinations of things. 

The number of "Permutations" of a system is the number of options when the order matters.  
The number of "Combinations" of a system is the number of options when the order doesn't matter.  
Both permutations and combinations can be computed with and without repetition.

When repetition is not permitted, the number of choices is reduced after each choice.  
e.g., If you Draw an Ace from a Deck of Cards, you reduce the Number of Aces Remaining in the Deck

How Many Different Ways are there to Shuffle a Deck of 52 Cards? 52!
How many different ways are there to choose 2 cards from a deck of 52 cards? $\frac{52!}{50!}$


When $r$ things are being chosen from a collection of $n$ things, the number of different permutations (where ORDER MATTERS) is: $$\frac{n!}{(n-r)!}$$
What if order doesn’t matter? $$\frac{n!}{r!(n-r)!}$$
**Combinatorics Notation** $$\binom{n}{k} = _{n}C_{r} = \frac{n!}{r!(n-r)!}$$
Example: Choosing BG3 party
4 Party Slots
6 Characters $$\binom{6}{4} = \frac{6!}{4!(6-4)!} = \frac{720}{48} = 15$$
 
---
## Permutations

#### **Without Repetition**
Each item can be used **at most once**. $$P(n, r) = \frac{n!}{(n-r!)}$$
- n = total items
- r = how many you're arranging

**Example**: How many ways to arrange 3 books on a shelf from 5 books? $$P(5, 3) = \frac{5!}{(5-3)!} = \frac{120}{2} = 60$$


#### **With Repetition**
Each item can be used **multiple times**. $$n^r$$
**Example**: How many 4-digit PINs using digits 0-9? $$10^4 = 10,000$$


---
## Combinations

#### Without Repetition
Selecting items where order doesn't matter, each used at most once. $$C(n, r) = \binom{n}{r} = \frac{n!}{r!(n-r)!}$$
**Example**: How many ways to choose 3 students from 10 for a committee? $$C(10, 3) = \binom{10}{3} = \frac{10!}{3!(10-3)!} = \frac{720}{6} = 120$$

#### With Repetition
Selecting items where order doesn't matter, but repetition is allowed. $$C(n + r-1, r) = \frac{n+r-1}{r!(n-1)!}$$
**Example**: How many ways to choose 3 scoops of ice cream from 5 flavours (can repeat flavours)? $$C(5+3-1, 3) = \frac{5+3-1}{3!(5-1)!} = \frac{7!}{3!4!} = 35$$



