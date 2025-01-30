Divisibility for remainder 0.

**1 :** 
	If its an integer, its divisibly by 1...

**2 :**
	If the number is even (2k), then it is divisible by 2.

**3 :**
	If the sum of the digits within the number is divisible by 3, then the original number is divisible by 3.

Proof :
$$abc = 100a + 10b + c = (a+b+c) + (99a + 9b)$$
Since $(99a + 9b)$ is always divisible by 3, if $(a + b + c)$ is divisible by 3, then the entire number is.

**4 :**
	If the number created from the last two digits of the original number is divisible by 4, then the original number is divisible by 4.

**5 :**
	If the number ends in 0 or 5, then it is divisible by 5.

**6 :**
	If the number is divisible by 3 AND the number is even, then it is divisible by 6.

**7 :**
	Separate the 1's place digit and multiply it by 2.
	Subtract the number from the remaining digits of the separated number.
	Repeat until you have a number that you can determine whether it is divisible by 7.
	If it is divisible by 7, then the original number is divisible by 7.

**8 :**
	Take the last three digits of the number.
	Multiply the 100's place digit by 4.
	Multiply the 10's place digit by 2.
	Take the results of those two products and sum them together with the 1's place digit.
	If the sum of those numbers is divisible by 8, then the original number is divisible by 8.

**9 :** 
	If the sum of the digits within the number is divisible by 9, then the original number is divisible by 9.