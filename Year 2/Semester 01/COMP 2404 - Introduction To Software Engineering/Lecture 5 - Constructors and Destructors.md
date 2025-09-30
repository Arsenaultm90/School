#### Default Arguments 

In **C++**, _default arguments_ let you give a function parameter a value that will be used automatically if the caller does not provide one.

**Syntax**
Default arguments are specified in the **function declaration** or **function definition** by assigning a value to a parameter:
```
void greet(std::string name = "Guest") {
    std::cout << "Hello, " << name << "!" << std::endl;
}

greet();            // Output: Hello, Guest!
greet("Alice");     // Output: Hello, Alice!
```


**Key Rules**
1. **Default values are assigned at the declaration point**  
    Usually, you put them in the _function prototype_ in a header file, not in both declaration and definition:
```
void display(int a, int b = 10); // declaration with default
void display(int a, int b) {     // definition (no default here)
    std::cout << a << " " << b;
}
```

2. **Defaults must be trailing**  
	Once you assign a default to one parameter, all parameters after it must also have defaults:
```
void example(int x, int y = 5, int z = 10); // valid
// void example(int x = 5, int y); // invalid
```

3. **Evaluation happens at the call site**  
    The compiler substitutes the default value at the place where the function is called.

4. **Works with different parameter types**  
    Defaults can be constants, variables with static storage, or even function calls:
```
int get_default() { return 42; }
void print(int x = get_default());
```


---
#### Default Member Functions

**The Four Default Member Function :**
1. **Default Constructor**
- A constructor with no parameters (or all parameters defaulted).
- Initializes objects without arguments.

```
class A {
public:
    A(); // generated automatically if you don't define any constructor
};
A obj; // works due to default constructor
```


2. **Copy Constructor**
- Creates a new object as a copy of an existing one.

```
class A {
public:
    A(const A& other); // generated automatically
};
A obj1;
A obj2 = obj1; // calls copy constructor
```


3. **Copy Assignment Operator** (`operator=`)
- Assigns values from one object to another _after both already exist_.

```
class A {
public:
    A& operator=(const A& other); // generated automatically
};
A obj1, obj2;
obj2 = obj1; // calls copy assignment
```

4. **Destructor**
- Cleans up when an object goes out of scope.

```
class A {
public:
    ~A(); // generated automatically
};
{
    A obj; // destructor called at block end
}
```


**Invocation Order:**
Create → Copy/Create → Assign → Destroy

**Explanation of Order:**
1. Default constructor runs when an object is first created without a copy.
2. Copy constructor runs when a new object is created from an existing one.
3. Copy assignment runs when an existing object is assigned another object.
4. Destructor runs **last**, in reverse order of construction, when objects go out of scope.
