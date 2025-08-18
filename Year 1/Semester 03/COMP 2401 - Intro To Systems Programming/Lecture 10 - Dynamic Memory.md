#### Double Pointers  

A **double pointer** is a pointer to another pointer. It is declared using `**`.
	`int **ptr;`

This means:
	`ptr` is a pointer to a pointer to an integer.
	Used when you want to **store the address of another pointer**.

| Use Case                        | Explanation                                                         |
| ------------------------------- | ------------------------------------------------------------------- |
| Dynamic 2D arrays               | You can allocate arrays of pointers to arrays (matrix)              |
| Modifying pointers in functions | Allows a function to change the actual pointer (not just the value) |
| Arrays of strings               | Often declared as `char **argv`                                     |
| Complex data structures         | e.g., pointer to pointer to struct for linked lists or trees        |

##### Double Pointer with 2D Arrays
```
int **matrix;
matrix = malloc(rows * sizeof(int *));
for (int i = 0; i < rows; i++) {
    matrix[i] = malloc(cols * sizeof(int));
}
```


##### Summary
`int *p` → pointer to int
`int **pp` → pointer to pointer to int
Dereferencing:
    `*pp` gives `p`
    `**pp` gives value of `value`



---
#### Collections

Static collection: Fixed size, allocated at compile time  
Dynamic collection: Size can change, allocated at runtime  
Elements:  
	Could be of any type  
	Could be pointers to any type


**How do we store things?**  
1. Arrays  
	Advantages:
		Fast access to elements  
		Easy to implement  
		Good cache performance  
	Disadvantages:  
		Cannot be resized  
		Wasted space if not full

2. Dynamic Arrays  
	Advantages:  
		Can grow and shrink as needed  
		More flexible than static arrays  
	Disadvantages:  
		Slower than static arrays due to resizing  
		More complex implementation

3. Linked Lists
	Advantages:  
		Can grow and shrink as needed  
	Disadvantages:  
		Slower access to elements  
		More complex implementation  
		Extra memory overhead for pointers  
		Cache performance is worse than arrays


```
struct SLLNode {  
	struct Student data;  
	struct Node *next;  
};  

struct DLLNode {  
	struct Student data;  
	struct DLLNode *next;  
	struct DLLNode *prev;  
};
  
struct StudentList {  
	struct Node *head;  
	struct Node *tail;  
};
```



