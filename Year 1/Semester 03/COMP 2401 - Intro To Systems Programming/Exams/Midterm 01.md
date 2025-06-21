Which of the following snippets of code best demonstrates good practice when using `scanf()` to read in a user-provided file name in order to avoid potential buffer overflows, assuming the file name will not contain spaces and that more user input will be collected later?

char filename[20];  
scanf("%19s", filename);  
while (getchar() != '\n');


---
When building, _Compilation_ refers to the process which:

Takes in many source code files and combines them into one object code file


---
Given code snippets A and B:
```
A:   int count = 0;  
   while (count < 5) {  
     if (count == 3) continue;  
     ++count;  
   }

B:   int count;  
   for (count=0; count < 5; ++count) {  
     if (count == 3) continue;  
   }
```

which of the following statements is true:

A causes an infinite loop, but B does not


---
The following can be executed **directly** by the computer:

machine code only


---
Given the statements:
`int count;  while ( (count=1)++ != 5);`

the above while statement contains how many operators (note: the `()` here are not considered :

3


---
Given code snippets A and B:
```
A:   int count = 0;  
   while (count < 5) {  
     if (count == 3) break;  
     ++count;  
   }

B:   int count;  
   for (count=0; count < 5; ++count) {  
     if (count == 3) break;  
   }
```


which of the following statements is true:

Neither A nor B causes an infinite loop


---
Given the statement:
`char b = 0xc7 - 0b00010001;`

what does the following statement output: printf("%d\n", b);

-74


---
Given the statement:
`char b = 0xc7 - 0b00010001;`

what binary sequence is stored in memory for variable b:

1011 0110


---
Given the statement:
`unsigned char a = 0x9d + 80;`

what binary sequence is stored in memory for variable a:

1110 1101


---
Given the statement:
`unsigned char a = 0x9d + 80;`

what does the following statement output: printf("%d\n", a);

237


---
Given the statements:
```
unsigned char a, b;  
a = 0263;  
b = a << 2
```

what does the following statement output:  printf("%d\n", b);

204


---
Given the statements:

```
char a, b;  
a = -109;  
b = a >> 2
```

what does the following statement output:  printf("%d\n", b);

-28


---
Given the program:
```
int main()  
{  
	char arr[32];  
	strcpy(arr, "Hello world");  
	printf("%d\n", arr);  
}
```

what is printed out on execution:

the address of the array


---
Given the program:
```
int main()  
	{  
	char arr[32];  
	strcpy(arr, "Hello world");  
	printf("%s\n", arr[4]);  
}
```

what is printed out on execution:

a runtime error occurs


---
Given the statements:
```
char str1[32];  
char str2[32];  
  
strcpy(str1, "Hello world");  
strcpy(str2, "Hello world");  

if (str1 == str2)  
	printf("test #1\n");  

if (strcmp(str1, str2) == 0)  
	printf("test #2\n");  
```

what do lines (7) and (10) do:

line (7) compares string addresses and line (10) compares string contents


---
Given the following union definition, how many bytes would the union reserve when it is initialized on an environment such as our course VM where we have 32-bit integers on a 64-bit machine?

```
union SensorData {
    int     humidity;
    float   temperature;
    char    motion;
};

union SensorData my_thermal_data;
```

4 bytes


---
Based on our discussions in class about how structures are organized in memory and given our 64-bit course programming environment, what would be the size of the structure `Container` when correctly instantiated (e.g., with `Container c;`)?

```
struct Item {
    float value;
  	int weight;
    float volume;
    int id;
};

struct Container {
    struct Item *item;
    int count;
};
```


