##### Statements(Proposition)
A **Statement/Proposition** is a sentence that is either true or false, but not both.

Ex.$$\displaylines{2 + 2 = 4\; |\; True \\ 2 + 2 = 5\;|\; False}$$

---
##### Compound Statements
Two or more statements compounded together by **Logical Connectives**.

**Logical Connectives:** $$\displaylines{Conjunction\;AND: \land \\Disjunction\; OR: \lor\\ NEGATION: \neg}$$
Ex.$$\displaylines{(p)\;My\;brother,\;John,\;is\;a\;student.\\
(q)\;3 + 5 = 8\\ \\
\neg p:\;My\;brother,\;John,\;is\;NOT\;a\;student.\\
p \land q:\;My\;brother,\;John,\;is\;a\;student\;AND\;3+5=8\\
p \lor q:\;My\;brother,\;John,\;is\;a\;student\;OR\;3+5=8\;}$$
**English - Logical Connectives**
but, nor $\rightarrow \land$

Ex. $$\displaylines{(p)\;It\;is\;cold\\
(q)\;It\;is\;cloudy\\ \\
It\;is\;not\;cold,\;but\;it\;is\;cloudy.\\
\neg p \land q}$$
---
##### Tautologies and Contradictions
**Tautology:** A statement that is always **True**.
**Contradiction:** A statement that is always **False**.

Ex.
Tautology: $p \lor \neg p$

| $p$ | $\neg p$ | $p \lor \neg p$ |
| --- | -------- | --------------- |
| 0   | 1        | 1               |
| 1   | 0        | 1               |

Contradiction: $p \land \neg p$

| $p$ | $\neg p$ | $p \land \neg p$ |
| --- | -------- | ---------------- |
| 0   | 1        | 0                |
| 1   | 0        | 0                |

---
##### Conditional Statements
If, ... then, ....
$p \rightarrow q \equiv \neg p \lor q$

Ex.$$\displaylines{p:\; work\;hard \\
q:\; get\;paid\\ \\
p \rightarrow q\\
If\;p,\;then\;q\\
If\;you\;work\;hard,then\;you\;get\;paid.}$$
**Negation Of Conditional Statements**
$$\displaylines{\neg(p \rightarrow q)\\
\neg(\neg p \lor q)\\
p \land \neg q}$$

**Contrapositive**$$\displaylines{p \rightarrow q \equiv \neg q \rightarrow \neg p}$$

---
##### Converse and Inverse
We have $p \rightarrow q$, therefore $$\displaylines{Converse:\;q \rightarrow p\\
Inverse:\;\neg p \rightarrow \neg q}$$
where, $$\displaylines{q \rightarrow p \equiv \neg p \rightarrow \neg q}$$

---
##### Biconditional Statements
If and Only If
$p \leftrightarrow q \equiv (p \rightarrow q)\land(q \rightarrow p)$

| $p$ | $q$ | $p \leftrightarrow q$ |
| --- | --- | --------------------- |
| 0   | 0   | 1                     |
| 0   | 1   | 0                     |
| 1   | 0   | 0                     |
| 1   | 1   | 1                     |

---
##### Quantified Statements
The representation of a **Statement/Proposition** using **Quantifiers**.

**ALL**
**Notation:** $\forall$
Universal Quantifier

Ex.$$\displaylines{A = \{1, 2, 3, 4, 5\}\\\forall x \in A\;|\;x>0 \\
For\;all\;x\;in\;A,\;every\;x\;is\;greater\;than\;0.}$$
**THERE EXIST**
**Notation:** $\exists$
Existential Quantifier

Ex.$$\displaylines{m = Any\; Integer\\
ℤ = Set\;of\;all\;Integers\\
\exists m \in ℤ\;|\;m^2 = m\\
There\;exists\;some\;m\;in\;the\;set\;of\;ℤ\;where\;m^2=m.}$$
**Negation of Quantified Statements**
All men wear hats.
	$x$ = men
	$Q(x)$ = Wear hats
	∴$\forall x \in A,\;Q(x)$

There exists a man that does not wear a hat.
	$\neg(\forall x \in A,\;Q(x))$
	$\exists x \in A, \neg Q(x)$

---
