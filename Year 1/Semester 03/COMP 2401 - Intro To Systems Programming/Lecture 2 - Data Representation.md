#### Number Representation and Bit Models
![[Screenshot 2025-05-21 at 1.52.44 PM.png]]

![[Screenshot 2025-05-21 at 1.53.00 PM.png]]

#### Conversions
![[Screenshot 2025-05-21 at 1.54.50 PM.png]]
![[Screenshot 2025-05-21 at 1.55.13 PM.png]]

![[Screenshot 2025-05-21 at 1.56.08 PM.png]]

```
#include <stdio.h>  

int main() {  
		unsigned char dec = 27; // = (2*10) + 7 = 27  
		unsigned char oct = 027; // = (2*8) + 7 = 23  
		unsigned char hex = 0xbf; // = (11*16) + 15 = 191  
		unsigned int hex2 = 0xbad; // = (11*256) + (10*16) + 13 = 2989  
		unsigned char bin = 0b00111100; // = (32 + 16 + 8 + 4) = 60  
		
		printf("%d %d %d %d %d\n", dec, oct, hex, hex2, bin);  
		
	return 0;  
}
```


---
#### Bit Models

**Magnitude-only Bit Model**
This model is for non-negative decimal numbers (whole numbers). With an 8-bit value, we can store a value in the range of 0 to 255

In this representation, we consider the leftmost bit to be considered the most-significant bit  
and the rightmost bit as the least-significant bit. (e.g., **1**011010**1**)

| Word Size   | Bits Used | Bytes Used | Number Range                    | C-Data Type        |
| ----------- | --------- | ---------- | ------------------------------- | ------------------ |
| byte        | 8         | 1          | 0 to 255                        | unsigned char      |
| 16-bit Word | 16        | 2          | 0 to 65,535                     | unsigned short int |
| 32-bit Word | 32        | 4          | 0 to 4,294,967,295              | unsigned int       |
| 64-bit Word | 64        | 8          | 0 to 18,446,744,073,709,551,615 | unsigned long int  |


**Sign-Magnitude Bit Model**  
This model allows negative decimal numbers (whole numbers). It is the simplest strategy for  
representing negative numbers. This allows numbers only in the range of **-127 to +127** for a single byte.

01111110 = 126  
01111111 = 127  
10000000 = -0  
10000001 = -1  
10000010 = -2  
...  
11111110 = -126  
11111111 = -127

If the signs differ, we need to subtract the smaller magnitude from the larger magnitude, and  
keep the sign of the larger magnitude.
- Step 1: Find the 1's complement of the subtrahend, which means the second number of subtraction.
- Step 2: Add it with the minuend or the first number.
- Step 3: If there is a carryover left then add it with the result obtained from step 2.
- Step 4: If there are no carryovers, then the result obtained in step 2 is the difference of the two numbers using 1's complement binary subtraction.

Example of (126 + -7)  :
	01111110 - 10000111 = 01110111 = 119



**Two’s Compliment Bit Model**  
This model allows both positive and negative decimal numbers (whole numbers).
Allows numbers only in the range of -128 to +127.
To represent negative numbers ... we take the bits that represent the number as if it were  
positive, then invert (or flip) all of the bits and then add 1. $$\displaylines{19 =\\ 00010011\\
11101100 \\
11101101}$$

| C - Data Type                          | Bits Used | Bytes Used | Number Range                                                  |
| -------------------------------------- | --------- | ---------- | ------------------------------------------------------------- |
| char<br>signed char                    | 8         | 1          | -128 to 127                                                   |
| short int<br>signed short int          | 16        | 2          | -32,768 to +32,767                                            |
| int<br>signed int                      | 32        | 4          | -2,147,483,648 to +2,147,483,647                              |
| long<br>signed long<br>signed long int | 64        | 8          | -9,223,372,036,854,775,808 to  <br>+9,223,372,036,854,775,807 |


**Fixed-Point Bit Model**  


Floating-Point Bit Model  

ASCII and Unicode Bit Model


