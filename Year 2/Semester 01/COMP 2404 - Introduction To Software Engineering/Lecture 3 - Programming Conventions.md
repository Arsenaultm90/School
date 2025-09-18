**Reasons for coding conventions:**
	Makes code easier to read.  
	Makes interfaces consistent.  
	If I expect a constant reference, that is what I should find.  
	Helps your code communicate with the code from the rest of the team.


---
#### Naming Conventions

Constants : UPPERCASE
Variables names :
	camelCase : numElements
	underscore : num_elements

Variable names should be self documenting.
	Storing a name : string name (not string n)
	Student id in a class Student : int id

Single lower case letters for loops : i, j, k, l

Data Types or Classes begin with uppercase.

Functions start in lowercase : `fooBar(){}`


---
#### Indentation

White space before the first character of the line. 
	Promotes readability  
	Usually used to denote blocks  
	{} braces tell the compiler where the blocks are,  
	indentation tells other programmers where the blocks are.


---
#### Blocks

**Block:**  
	Sequence of statements between a pair of braces {}.  

**Nested block:**  
	Block within another block.  
	Should have extra indentation.  

**Nesting level of a block:**  
	The number of open and not yet closed braces before a block.  
	Depth from file scope.

**Indentation Rules for Blocks**  
All statements within a block should have the same (indentical!) indentation.  
All blocks at the same nesting level should have identical indentation.

**Indentation Rules**  
There are three acceptable styles of brace indentation.  
This is for consistency of communication between programmers. 

```
if (bool)
{
	// Some Stuff
}

if (bool) {
	// Some stuff
}

if (bool) { // Some stuff}
```


**Indentation Convention:**  
	2 spaces.  
	4 spaces.  
	One tab (not always portable between editors).


---
#### Comment Blocks

Blocks of comments are used to :  
	Explain the program  
	Explain a class
	Explain a complex or critical block or section of code

Block of comments in the main function specify :
	- The purpose of program
	- How to use it  
	- The authors
	- All revisions


---
#### Comments

Each class should have a block of comments before the class definition describing the purpose of the class, or any functions or variables that require additional information.  

**Inline comments:**  
Should be short – one line, or part of a line, or two short lines.  
```
int x = input(); // input from keyboard  
// this expression finds the intersection of two lines in  
// the form m = ax+b  
intersect = <some expression>
```


Larger blocks of comments are used to explain a class, or explain a section of code that might be confusing.  

```
/*  
* If I need a paragraph to explain something,  
* I can use this style of comments.  
* The * to begin each line is cosmetic, but encouraged.  
* When we are finished we end with  
*/
```


---
#### Other Conventions

1. Don’t use structs when you should use classes..  
2. Don’t use global variables.  
3. Don’t use too many global functions  
4. In some cases they are needed, because C++.  
5. Don’t pass objects (classes) by value.  
6. This makes copies, it is slow and wasteful of memory.  
7. DO reuse code whenever possible.  
8. Don’t copy and paste code over and over – if you are doing this it is time to refactor .  
9. DO perform basic error checking  
10. Sanitize any data that goes into your class.

