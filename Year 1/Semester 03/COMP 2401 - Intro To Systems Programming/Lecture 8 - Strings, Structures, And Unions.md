#### Strings

A “string” in C is just an array of characters.
NULL Terminator: The 0 at the end of a character array.

**Example :**
`char my_str[] = {'A', 'b', 'c', 'd', 0};`

| Address | Value |
| ------- | ----- |
| 0x0001  | 'A'   |
| 0x0002  | 'B'   |
| 0x0003  | 'C'   |
| 0x0004  | 'D'   |
| 0x0005  | '\0'  |

##### String Functions
```
#include <string.h>  

size_t strlen(const char *)  
int strncmp(const char *a, const char *b, size_t n)  
char* strncpy(char *dest, const char *src, size_t n)  
char* strncat(char *dest, const char *src, size_t n)
```



---
#### Structures

A `struct` is a **user-defined data type** that allows grouping variables of **different types** under a single name.

**Syntax :**
```
struct Student {
    char name[50];
    int age;
    float gpa;
};
```

**Declare and Initialize :**
```
struct Student s1;  // declare a struct variable

// Initialize manually
strcpy(s1.name, "Alice");
s1.age = 20;
s1.gpa = 3.75;

// Initialize using initializer list
struct Student s2 = { "Bob", 21, 3.9 };
```

**Accessing Struct Member (Direct vs Pointer) :**
```
// Direct
struct Student s = { 20 };
s.age

// Pointer
struct Student *p = &s;
p->age
```


##### Padding
Most systems **align data** in memory so that types like `int` start at an address that’s a multiple of their size — for performance reasons.


```
struct stu {
    char a;  // 1 byte
    int b;   // 4 bytes
};
```

- `char a` takes **1 byte**
- But `int b` needs to start at a **4-byte aligned address**
- So the compiler adds **3 bytes of padding** between `a` and `b`

So now :
```
printf("%zu\n", sizeof(struct stu));  // prints 8
```


---
#### Typedef
`typedef` in C is used to **create an alias (nickname) for a data type**. It doesn’t create new types — it just gives existing ones **shorter or more meaningful names**.


```
struct student {  
char first[STR_MAX];  
char last[STR_MAX];  
int id[ID_MAX];  
float gpa;  
};  
  
typedef struct student Student;  

int main(void) {  
Student anakin = {"Anakin", "Starkiller", 10066, 8.2};  
struct student obiwan = {"Obiwan", "Kenobi", 10011, 11.5};  
}
```



---
#### Unions

A `union` in C is a special data type that lets you **store different types in the same memory location**, but **only one at a time**. 

It’s like a `struct`, but instead of **each member having its own space**, **all members share the same memory**.


**Example :**
```
union Data {
    int i;         // 4 bytes
    float f;       // 4 bytes
    char str[20];  // 20 bytes
};
```

The size of the union is **the size of its largest member** — here, `str[20]` → **20 bytes total**.






