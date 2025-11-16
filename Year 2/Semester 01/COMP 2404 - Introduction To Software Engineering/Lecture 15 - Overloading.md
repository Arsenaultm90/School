#### **Function Overloading**

**Function overloading** means having **multiple functions with the same name**, but with **different parameter lists**.

The compiler determines _which version to call_ based on:
- number of parameters
- types of parameters
- order of parameters

This is a **compile-time** feature — also known as **static polymorphism**.

Example:
```
void print(int x) {
    cout << "int: " << x << endl;
}

void print(double x) {
    cout << "double: " << x << endl;
}

void print(string s) {
    cout << "string: " << s << endl;
}
```

Calling them:
```
print(10);       // calls print(int)
print(3.14);     // calls print(double)
print("hello");  // calls print(string)
```
The compiler chooses the correct version **before runtime**.


---
Operator Overloading

C++ allows you to define what built-in operators mean for **your own classes**.

Example:
```
class Vector2 {
public:
    Vector2() : x(0), y(0) {}
    Vector2(float x, float y) : x(x), y(y) {}
    Vector2(float both) : x(both), y(both) {}
};
```


Example operators:
- `+`, `-`, `*`, `/`
- `==`, `!=`
- `<`, `>`
- `[]`
- `()`
- `<<`, `>>`
- assignment `=`
- increment `++`
- dereference `*`
- arrow `->`

Operator overloading is also **compile-time polymorphism**.

Example:
```
#include <iostream>
using namespace std;

class Vector2 {
public:
    float x, y;

    Vector2(float x = 0, float y = 0) : x(x), y(y) {}

    /*------------------------------
      1. Arithmetic Operators
    ------------------------------*/
    Vector2 operator+(const Vector2& other) const {
        return Vector2(x + other.x, y + other.y);
    }

    Vector2 operator-(const Vector2& other) const {
        return Vector2(x - other.x, y - other.y);
    }

    Vector2 operator*(float scalar) const {
        return Vector2(x * scalar, y * scalar);
    }

    Vector2 operator/(float scalar) const {
        return Vector2(x / scalar, y / scalar);
    }

    // Unary minus
    Vector2 operator-() const {
        return Vector2(-x, -y);
    }

    /*------------------------------
      2. Comparison Operators
    ------------------------------*/
    bool operator==(const Vector2& other) const {
        return x == other.x && y == other.y;
    }

    bool operator!=(const Vector2& other) const {
        return !(*this == other);
    }

    bool operator<(const Vector2& other) const {
        return (x*x + y*y) < (other.x*other.x + other.y*other.y);
    }

    bool operator>(const Vector2& other) const {
        return other < *this;
    }

    bool operator<=(const Vector2& other) const {
        return !(*this > other);
    }

    bool operator>=(const Vector2& other) const {
        return !(*this < other);
    }

    /*------------------------------
      3. Assignment Operator
    ------------------------------*/
    Vector2& operator=(const Vector2& other) {
        if (this != &other) {
            x = other.x;
            y = other.y;
        }
        return *this;
    }

    /*------------------------------
      4. Increment / Decrement
         prefix ++v and postfix v++
    ------------------------------*/
    // Prefix ++v
    Vector2& operator++() {
        x++; y++;
        return *this;
    }

    // Postfix v++
    Vector2 operator++(int) {
        Vector2 temp = *this;
        x++; y++;
        return temp;
    }

    /*------------------------------
      5. Subscript Operator []
    ------------------------------*/
    float& operator[](int index) {
        return (index == 0) ? x : y;
    }

    /*------------------------------
      6. Call Operator ()
      Pretend this computes dot product
    ------------------------------*/
    float operator()(const Vector2& other) const {
        return x * other.x + y * other.y;
    }
};

/*--------------------------------------
  7. Stream Operators
--------------------------------------*/
ostream& operator<<(ostream& os, const Vector2& v) {
    os << "(" << v.x << ", " << v.y << ")";
    return os;
}

istream& operator>>(istream& is, Vector2& v) {
    is >> v.x >> v.y;
    return is;
}

/*--------------------------------------
  8. Arrow Operator ->
  Only useful when your class wraps a
  pointer to another object.
--------------------------------------*/
class Wrapper {
public:
    Vector2* ptr;
    Wrapper(Vector2* p) : ptr(p) {}

    Vector2* operator->() {
        return ptr;
    }
};
```

Usage:
```
int main() {
    Vector2 a(1, 2);
    Vector2 b(3, 4);

    cout << "a + b = " << (a + b) << endl;
    cout << "a - b = " << (a - b) << endl;

    cout << "a * 2 = " << (a * 2) << endl;
    cout << "-a = " << (-a) << endl;

    cout << "Dot product = " << a(b) << endl; // call operator

    cout << "a < b? " << (a < b) << endl;

    cout << "a[0] = " << a[0] << ", a[1] = " << a[1] << endl;

    ++a;
    cout << "After ++a: " << a << endl;

    a++;
    cout << "After a++: " << a << endl;

    // Arrow operator example
    Wrapper w(&a);
    cout << "w->x = " << w->x << endl;

    return 0;
}
```
