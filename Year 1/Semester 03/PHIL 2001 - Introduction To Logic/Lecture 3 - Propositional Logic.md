It investigates the relationships among entire propositions to determine the validity of arguments.


---
#### Notation

**Variables**
Only CAPITAL letters, standing for complete  PROPOSITIONS.
Propositions = units that can take a truth value (can be either TRUE or FALSE).

**Operators(Connectives)**
Negation (~), Conjunction (•), Disjunction(∨), Conditional (⊃) and Biconditional(≡).  
These are truth-functional operators.


---
#### Translations

| Notation                                                                         | Example                                                                                 | Symbol |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | ------ |
| Simple Propositions                                                              | I am bored.                                                                             | B      |
| Negations: no, not, never                                                        | Dolphins aren’t fish.                                                                   | ~D     |
| Conjunctions: and, but, yet, however, nonetheless                                | Paris is a city and France is a country.                                                | P • F  |
| Disjunctions: or, either...or, choice between ... and ...                        | You can have either the  <br>soup or the salad.                                         | P ∨ D  |
| Conditionals: if...then, implies, only if                                        | If you don’t study, you  <br>will fail.                                                 | ~S ⊃ F |
| Biconditionals: if and only if, iff, necessary and sufficient condition, just if | The object will fall if and  <br>only if it is subject to the  <br>gravitational force. | O ≡ G  |

| Conditionals (If... Then) |     |           |
| ------------------------- | --- | --------- |
| A                         | B   | (A $⊃$ B) |
| 0                         | 0   | 1         |
| 0                         | 1   | 1         |
| 1                         | 0   | 0         |
| 1                         | 1   | 1         |

| Biconditional(IF and ONLY IF) |     |         |
| ----------------------------- | --- | ------- |
| A                             | B   | (A ≡ B) |
| 0                             | 0   | 1       |
| 0                             | 1   | 0       |
| 1                             | 0   | 0       |
| 1                             | 1   | 1       |


---
#### Equivalence Rules

**Commutation :** 
	(A · B) = (B · A)
	(A ∨ B) = (B ∨ A)
	(A $\equiv$ B) = (B $\equiv$ A)

**Association :**
	((A · B) · C)  = (A · (B · C))
	((A ∨ B) ∨ C) = (A ∨ (B ∨ C))
	((A $\equiv$ B) $\equiv$ C) = (A $\equiv$ (B $\equiv$ C))

**Contraposition :**
	(A $⊃$ B) = (~B $⊃$ ~A)

**DeMorgan :**
	~(A · B) = (~A ∨ ~B)
	~(A ∨ B) = (~A · ~B)

**Implication :**
	(A $⊃$ B) = (~A ∨ B)
	(A ∨ B) = (~A $⊃$ B)


---
#### Argument Validity

##### Truth Tables
To test the **validity of an argument using truth tables**, you're checking if the **conclusion must be true whenever all the premises are true**.

If **even one row** exists where:
- All premises are **true**
- The conclusion is **false**
	→ then the argument is **invalid**.
	

**Example :**
Premises:
1. P → Q
2. Q

Conclusion:  
∴ P

| P   | Q   | P → Q | ∴ P | All Premises True? | Valid Row?                            |
| --- | --- | ----- | --- | ------------------ | ------------------------------------- |
| T   | T   | T     | T   | ✅                  | ✅                                     |
| T   | F   | F     | T   | ❌                  | —                                     |
| F   | T   | T     | F   | ✅                  | ❌ → conclusion is false → **invalid** |
| F   | F   | T     | F   | ❌                  | —                                     |


---
#### Harder Translations

But, although, however, yet, also ... = AND
Unless = OR
Given that, presuming that, assuming that, provided that, ...  = IF
	A is SUFFICIENT for B = (A -> B)
	A is NECESSARY for B = (~A -> ~B) = (B -> A)
Iff, necessary and sufficient, just if = IF AND ONLY IF

What’s after “if” is the 1st part of the conditional (IF = 1st)  
What’s after “only if” is the 2nd part of the conditional (ONLY IF = 2nd)  



