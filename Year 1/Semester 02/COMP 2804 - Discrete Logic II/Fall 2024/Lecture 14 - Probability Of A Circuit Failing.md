#### Circuits

For each $i \in \{1, \dots, n\}$, $E_i$ = "The circuit is working"
Assume : $E_{1}, E_{2}, \dots, E_{n}$ are mutually independent.
For each $i \in \{1, ..., n\}$, $P(E_i) = p$


**Sequential Circuits** (Not Reliable)
![[Drawing 2025-03-11 07.19.02.excalidraw.png]]

P("The whole circuit works") = $$\displaylines{P(E_{1}\cap E_{2} \cap E_{3} \cap \dots \cap E_{n}) \\ 
P(E_{1}) ·P(E_{2}) · \dots · P(E_{n}) \\
P^n}$$
Example : $$\displaylines{p = \frac{1}{2} \\
n = 10 \\
P(\text{"The whole circuit works"}) = \left( \frac{1}{2} \right)^{10} = \frac{1}{1024}}$$


**Parallel Circuits**
![[Drawing 2025-03-11 07.32.41.excalidraw.png|500]]

$P(E_{1} \cup E_{2} \cup \dots \cup E_{n})$ :$$\displaylines{ =1 - P(\overline{E_{1}} \cap \overline{E_{2}} \cap \dots \cap \overline{E_{n}}) \\
= P(\overline{E_{1}})·P(\overline{E_{2}})· \dots · P(\overline{E_{n}}) \\
=1 - (1-p)^n}$$
Example :$$\displaylines{p = \frac{1}{2} \\
n = 10 \\
P(\text{"The whole circuit works"}) = 1-(1-p)^{10} = \frac{1023}{1024}}$$


---
#### Reservoir Sampling (Algorithm R)

Reservoir Sampling is a **randomized algorithm** used to select **a random subset** of k items from a data stream of unknown length n, ensuring that each item has an equal probability of being chosen. It allows processing data in a **single pass** using **constant memory**.

For the special case where k=1, the algorithm ensures that **each item has a 1/n probability of being the final selection**, even though n is unknown in advance.

 **Key Properties:**
1. **Single-pass processing** – The algorithm processes each element **one at a time**, making it efficient for streaming data.
2. **Equal probability** – Every element has an equal chance of being selected.
3. **Constant space O(k)** – Only k selected elements are stored at any time, regardless of n.

```
i = 1

while s.hasMoveData() {
	x = s.nextData();
	k = randomInt(1, ... , i);

	if (k = 1) {
		z = x  // (*) executes with probability of 1/i
	}
	i++;

	// n == i;
	return z;
}
```


Claim : For any $i \in \{1, \dots, n\}$, P("Algorithm outputs $x_i$") = $\frac{1}{n}$.
For each $i \in \{1, \dots, n\}$, let $E_{i}$ = "Line * executes on iteration $i$" $$\displaylines{x_{1}, x_{2} , x_{3}, \dots, x_{i}, x_{i+1}, x_{i+2}, \dots, x_{n}\\ \text{"algorithm outputs } x_{i}\text{"} = E_{i} \cap \overline{E}_{i+1} \cap \overline{E}_{i+2} \cap \dots \cap \overline{E}_{n}}$$
$$\displaylines{P(\text{"Algorithm outputs } x_{i}\text{"}) = P(E_{i} \cap \overline{E}_{i+1} \cap \overline{E}_{i+2} \cap \dots \cap \overline{E}_{n}) \\
=P(E_{i})·P(\overline{E}_{i+1}) · \dots · P(\overline{E}_{n}) \\
=\frac{1}{i}·\left( 1 - \frac{1}{i+1} \right)·\left( 1 - \frac{1}{i+2} \right)·\dots ·\left( 1-\frac{1}{n} \right) \\
\frac{1}{i} · \frac{i}{i+1} ·\frac{i+1}{i+2}· \dots · \frac{n-2}{n-1} · \frac{n-1}{n}\\
= \frac{1}{n}}$$

