## Deep Copy Example:

```
Show::Show(const Show& show)
    : name(show.name),
      numEpisodes(show.numEpisodes),
      episodes(new Episode*[256])
{
    for (int i = 0; i < numEpisodes; ++i) {
        episodes[i] = new Episode(
            *show.episodes[i]   // copy the Episode object
        );
    }
}
```




## Constructor & Destructors

**Construction:** base classes → member objects → class  
**Destruction:** class → member objects → base classes


```
class Animal {
	public:
	Animal() { cout << "Animal ctor" << endl; }
	~Animal() { cout << "Animal dtor" << endl; }
};

class Bird : public Animal {
	public:
	Bird() { cout << "Bird ctor" << endl;  }
	~Bird() { cout << "Bird dtor" << endl; }
};

int main() {
	Animal animal;
	Bird bird;
}


// OUTPUT
Animal ctor    ← for Animal animal
Animal ctor    ← base part of Bird bird
Bird ctor
Bird dtor
Animal dtor    ← base part of Bird bird
Animal dtor    ← Animal animal
```




## Cascading Method Calls (Method Chaining)
Method chaining works by having each function return the current object (usually by reference), allowing subsequent method calls to operate on that same object.

```
// ORIGINAL
void setDay(int);
void setMonth(int);
void setYear(int);
void setDate(int, int, int);
void setDate(Date&);


// NEW
Date& setDay(int);
Date& setMonth(int);
Date& setYear(int);
Date& setDate(int, int, int);
Date& setDate(const Date&);


Date& Date::setDay(int d) {
    day = d;
    return *this;
}


// RESULT
Date d;
d.setYear(2025)
 .setMonth(12)
 .setDay(19);

```




## Diamond Hierarchy

![[Screenshot 2025-12-19 at 12.44.25 PM.png]]

#### No Default Constructor
If a base class has no default constructor, every derived constructor must explicitly call it.

#### Virtual Inheritance
Virtual inheritance ensures that only one shared instance of a base class exists in a diamond hierarchy, and that the most derived class is responsible for constructing it.

`virtual` means **the version that matches the _actual object type_ at runtime is used**


```
class Animal {
	protected:
	    std::string name;
	public:
	    Animal(const std::string& n) : name(n) {}
};

class Human : public virtual Animal {
	protected:
	    int feet;
	public:
	    Human(int f) : Animal(""), feet(f) {}
};


class Goat : public virtual Animal {
	protected:
	    int feet;
	public:
	    Goat(int f) : Animal(""), feet(f) {}
};


class Centaur : public Human, public Goat {
	public:
	    Centaur(const std::string& n, int humanFeet, int goatFeet)
	        : Animal(n),      // ONLY HERE
	          Human(humanFeet),
	          Goat(goatFeet) {}
};

```



## Class Operators

**Given Class:**
```
class Time {
public:
    Time(int = 0, int = 0, int = 0);

private:
    int seconds, minutes, hours;
    int convertToSeconds() const;
};
```

#### Implementing the `+` operator
- `+` should **not modify either operand**
- It should return a **new `Time` object**
- Best implemented as a **member function** or **non-member friend**

```
Time Time::operator+(const Time& other) const {
    int totalSeconds =
        convertToSeconds() + other.convertToSeconds();

    int h = totalSeconds / 3600;
    totalSeconds %= 3600;
    int m = totalSeconds / 60;
    int s = totalSeconds % 60;

    return Time(h, m, s);
}

// USAGE
Time t3 = t1 + t2;
```


#### Implementing the `==` operator
- Equality should compare **logical value**, not raw members
- Use `convertToSeconds()` to avoid normalization issues

```
bool Time::operator==(const Time& other) const {
    return convertToSeconds() == other.convertToSeconds();
}

// USAGE
if (t1 == t2) { ... }
```


#### Comparing `Time` with an `int` using `==`
```
bool Time::operator==(int secs) const {
    return convertToSeconds() == secs;
}
```



## Object Design Categories
#### Entity (Domain / Model objects)
Represent real-world concepts and data.

#### Boundary (Interface objects)
Handle interaction with users or external systems.

#### Control (Controller objects)
Coordinate logic between objects.

Collection


## Design Patterns

#### Factory
Creates objects without exposing construction logic.
```
Animal* AnimalFactory::create(string type);
```

#### Singleton
Only one instance exists.
```
class Logger {
public:
    static Logger& instance();
};
```

#### Observer
Objects subscribe to changes.

#### Strategy
Change behaviour at runtime.

- **Creational** → “Who makes it?”
- **Structural** → “How are they connected?”
- **Behavioural** → “How do they talk to each other?”

## Iterators

```
#include <vector>
#include <iostream>
using namespace std;

vector<int> nums = {1, 2, 3, 4, 5};

for (vector<int>::iterator it = nums.begin();
     it != nums.end();
     ++it)
{
    cout << *it << endl;
}


// MODERN
for (auto it = nums.begin(); it != nums.end(); ++it) {
    cout << *it << endl;
}
```



## Variables, Pointers, Reference

#### Normal Variable
```
int x = 10;
```
- One piece of data: `10`
- Stored somewhere in memory

#### A Pointer
```
int* p = &x;
```
- `x` → the integer
- `p` → stores the address of `x`

#### A Reference
```
int& r = x;
```
- `r` is an **alias**, not new data
- No new memory created

#### Reference to Pointer
```
int*& rp = p;
```
- `rp` aliases `p`
- Still points to `x`

#### Invalid Reference
```
int& bad; // references must be initialized
```


## Const = 0
- `= 0` → **pure virtual function**
    - Makes the class **abstract**
    - Forces derived classes to implement it
- `const` → promises the function **does not modify the object**



## Programming w/ Templates


```
// Array . h
# ifndef ARRAY_H
# define ARRAY_H
# include < iostream >
# include < string >
# define MAX_ARRAY 256

using namespace std ;

template < class T >
class Array {
	public :
		Array ();
		~ Array ();
		// add T to the back of the array if there is room
		Array <T >& operator +=( const T &);
		// remove T if it exists
		Array <T >& operator -=( const T &);
		// return element at index , or call exit (1) on bad index
		T & operator []( int index );
		const T & operator []( int index ) const ;
		// inline functions
		int size () const { return numElements ; }
		bool isFull () const { return numElements >= MAX_ARRAY ;}
	private :
		int numElements ;
		T* elements ;
};
```


#### Constructor
```
template <class T>
Array<T>::Array() : numElements(0) {
    elements = new T[MAX_ARRAY];
}
```


#### Destructor
```
template <class T>
Array<T>::~Array() {
    delete[] elements;
}
```


#### operator+=
```
template <class T>
Array<T>& Array<T>::operator+=(const T& item) {
    if (isFull()) {
        return *this;
    }

    elements[numElements++] = item;
    return *this;
}
```


#### operator-=
```
template <class T>
Array<T>& Array<T>::operator-=(const T& item) {
    for (int i = 0; i < numElements; ++i) {
        if (elements[i] == item) {
            // shift left
            for (int j = i; j < numElements - 1; ++j) {
                elements[j] = elements[j + 1];
            }
            numElements--;
            break;
        }
    }
    return *this;
}
```


#### operator[]
```
template <class T>
T& Array<T>::operator[](int index) {
    if (index < 0 || index >= numElements) {
        exit(1);
    }
    return elements[index];
}
```


#### operator[] const
```
template <class T>
const T& Array<T>::operator[](int index) const {
    if (index < 0 || index >= numElements) {
        exit(1);
    }
    return elements[index];
}
```



## Templates

Templates let you write **generic code** that works for **many types** without rewriting it.

The compiler **generates a version for each type** used.
	This happens at **compile time**.

`template <class T>` must be declared in the header.


**Basic Class Template :**
```
template <class T>
class Box {
public:
    Box(T v) : value(v) {}
    T get() const { return value; }
private:
    T value;
};

Box<int> b1(10);
Box<string> b2("hello");

cout << b1.get();
cout << b2.get();
```


**Operator Overload :**
```
template <class T>
class Array {
public:
    Array<T>& operator+=(const T& item);
};
```



## Return Values

By Value:
```
int makeInt() {
    int x = 5;
    return x;   // copy (or optimized away)
}
```


By Pointer
```
int* makeIntPtr() {
    int* p = new int(5);
    return p;   // caller must delete
}
```


Return pointer to existing object
```
int* getElement(int arr[], int index) {
    return &arr[index];
}
```


By Reference:
```
int& getRef(int& x) {
    return x;
}
```

