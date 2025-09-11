##### Software Engineering

Established practices for software engineering:  
Testing  
	Unit, integration, systems.  
	Ensures correctness.  
Modularity  
	 “Modules” of code with clear purpose and well-defined interfaces  
	Makes debugging and understanding your code easier.  
Documentation  
	Is your code readable? Do you have documentation for users?  
Good (often well-established) design  
	Making changes easy


---
##### Tools

**C++ Programming Language**  
	Using gcc compatible compiler  

**Linux Operating System**  
	Based on the Unix operating system  
	Developed in Bell Labs by Ken Thompson and Dennis Ritchie  
	MacOS is Unix-compliant
  
**Shell**  
	A Shell is an interface to the OS  
	Command line  
	Similar to Windows command line  
	Allows you to run commands on the OS  
	Look through file systems  
	Execute programs  
	Use weird, esoteric commands to look cool for your friends

**Common shells**
	Bourne shell (sh)  
	Bourne-again shell (bash) - this is the default shell for Linux  
	C shell (csh)

```
ls - list the files in the current directory  
cd - change directory  
chmod +x <file> - make <file> executable  
./<file> - (from same directory as <file>) execute <file>  
cat - write the contents of a file to the console  
grep - search a file for a string
```

Mac can use Clang, which is a drop in replacement for GCC


---
##### Programming Tools

**Compilation**  
	Turns C++ code into object code  
	1-to-1 correspondence between C++ source files and object files  

**Linking**  
	Connects object code together  
	Ex. Your source code may call a library function  
	When compiling object code that calls other libraries, the compiler only needs the  
	function signature – not the executable code  
	Executable code for the library function is in a different object file  
	“Linking” supplies the called function code to your compiled code


---
##### Build Tools

**Makefiles**
```
CC = gcc
CFLAGS =  -W -ansi -pedantic -Wall
FILES = Main.c Arg.c Banana.c
OUT_EXE = Main

build: $(OUT_EXE)

$(OUT_EXE): $(FILES)
$(CC) $(CFLAGS) -o $(OUT_EXE) $(FILES)

clean: rm -f *.o core *.exe *~

rebuild: clean build
```



---
#### Example C


```
#include <iostream>
using namespace std;

int main() {
	int var1;
	
	cout << "Hello World!" << endl;
	cin >> var1
}
```
