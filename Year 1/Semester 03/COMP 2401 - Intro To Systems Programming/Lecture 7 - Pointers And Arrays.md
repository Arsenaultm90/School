A **pointer** is a variable that stores the **memory address** of another variable

```
int x = 10;
int *p = &x;  // p is a pointer to an int, storing the address of x

// *p : Points to an address
// &x : Address of this variable
```


---
**Dereferencing** means accessing the value stored at the memory address the pointer holds:

```
int x = 10;
int *p = &x;

printf("%d\n", *p);  // Outputs 10
```


---
When you pass a variable to a function, it’s passed **by value**. The function gets a copy:

```
void increment(int x) {
    x++;
}

int main() {
    int a = 5;
    increment(a);
    printf("%d\n", a);  // Outputs 5
}
```


To allow the function to modify the original variable, pass a pointer:

```
void increment(int *x) {
    (*x)++;
}

int main() {
    int a = 5;
    increment(&a);       // pass address of a
    printf("%d\n", a);   // Outputs 6
}
```


---
#### Pointers and Arrays

Arrays and pointers are closely related in C.

```
int arr[] = {1, 2, 3};
int *p = arr;  // p points to arr[0]

printf("%d\n", *(p + 1));  // Outputs 2
```

- `arr` is treated as a pointer to the first element.
- `p + 1` moves the pointer to the next integer (4 bytes ahead).


Arrays are always passed by reference (as pointers), so the original is modified.

```
void doubleValues(int *arr, int size) {
    for (int i = 0; i < size; i++) {
        arr[i] *= 2;
    }
}

int main() {
    int data[] = {1, 2, 3};
    doubleValues(data, 3);

    for (int i = 0; i < 3; i++)
        printf("%d ", data[i]);  // Outputs 2 4 6
}
```


---
#### Pointers to Pointers

You can also have a pointer to a pointer:

```
int x = 5;
int *p = &x;
int **pp = &p;

printf("%d\n", **pp);  // Outputs 5
```

- Dynamically allocating 2D arrays.
- Passing a pointer and modifying its address (e.g., allocating memory inside a function)


