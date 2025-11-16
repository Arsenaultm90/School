#### **Streams**

A **stream** in C++ is an abstraction that represents a **flow of data**.  
Think of a stream as a sequence of bytes going **in** or **out** of a program.

C++ defines three major types:
- **Input streams** (read)
- **Output streams** (write)
- **Bidirectional streams** (read + write)

**Standard Streams (Predefined)**

|Stream|Type|Description|
|---|---|---|
|`std::cin`|istream|Standard input (keyboard)|
|`std::cout`|ostream|Standard output (screen)|
|`std::cerr`|ostream|Unbuffered error output|
|`std::clog`|ostream|Buffered error output|

##### Stream Classes
Located in `<iostream>` and related headers.

**Main classes**
- `std::istream` – general input
- `std::ostream` – general output
- `std::iostream` – both input/output

**Derived classes**
- `std::ifstream` – file input
- `std::ofstream` – file output
- `std::fstream` – file input/output

Input
```
int x;
std::cin >> x;
```

Output:
```
std::cout << "Hello\n";
```

Stream extraction and insertion operators
- `>>` extraction (input)
- `<<` insertion (output)

##### Streams use **buffering**
Output is often stored in a buffer first, then flushed to the terminal or file.
Flushing occurs when:
- `\n` is printed (sometimes)
- you call `std::flush`
- program ends normally
- the buffer gets full


---
#### **Files**

C++ handles files using the `<fstream>` library, which provides the following classes:
- `std::ifstream` — read from file
- `std::ofstream` — write to file
- `std::fstream` — read + write

##### Opening Files
```
std::ifstream fin("input.txt");
std::ofstream fout("output.txt");
std::fstream fio("data.txt");
```

You can also specify modes:
```
std::ofstream fout("data.txt", std::ios::app);
```


**File Open Modes:**

|Mode|Meaning|
|---|---|
|`std::ios::in`|open for reading|
|`std::ios::out`|open for writing|
|`std::ios::app`|append to end|
|`std::ios::ate`|open + go to end|
|`std::ios::trunc`|erase existing file|
|`std::ios::binary`|binary mode|

Example:
```
std::fstream file("data.bin",
    std::ios::in | std::ios::out | std::ios::binary);
```


##### Reading From A File
Line-By-Line:
```
std::string line;
while (std::getline(fin, line)) {
    std::cout << line << std::endl;
}
```

Word-By-Word:
```
std::string word;
while (fin >> word) {
    std::cout << word << "\n";
}
```

Numbers:
```
int x;
fin >> x;
```


##### Writing To A File
```
std::ofstream fout("output.txt");
fout << "Hello File!\n";
```

Always check if file opened:
```
if (!fout.is_open()) {
    std::cerr << "Failed to open file\n";
}
```


##### Closing A File
```
fin.close();
fout.close();
```

If you forget:
- File objects close automatically when they go out of scope.
- But explicitly closing shows intent (good style).


##### Binary File I/O
Binary I/O uses `read()` and `write()` which operate on raw bytes.

**Writing Binary:**
```
int n = 42;
fout.write(reinterpret_cast<char*>(&n), sizeof(n));
```

**Reading Binary:**
```
int n;
fin.read(reinterpret_cast<char*>(&n), sizeof(n));
```

This is important for:
- Structs
- Large data sets
- Non-text formats


---
#### **Error State Flags**

Streams track errors automatically using **state flags**.  
These flags describe whether the last I/O operation succeeded.

##### The four main flags are:
**1. `goodbit`**
- No errors
- Everything is fine

Check with:
```
if (stream.good()) { ... }
```

**2. `eofbit`** (End Of File)
Set when input tries to read **past** the end of a file.
```
if (fin.eof()) { ... }
```

Example:
```
int x;
while (fin >> x) { }  // reads until EOF
// Now eofbit is set
```

**3. `failbit`**
Set when an extraction fails due to **format mismatch** or invalid input.

Example:
```
int x;
std::cin >> x;   // user types: "hello"
```
- Cannot convert "hello" to int
- `failbit` is set

**4. `badbit`**
Serious, unrecoverable error:
- hardware failure
- corrupted stream
- failed read/write on device

```
if (fin.bad()) {
    // something very wrong happened
}
```


##### Clearing Error Flags
After a fail state, the stream becomes unusable until cleared:
```
std::cin.clear();       // clears failbit and badbit
std::cin.ignore(1000, '\n');  // skip bad input
```

##### Checking Multiple States:
```
if (!fin) {
    std::cout << "Something went wrong\n";
}
```
`!fin` is true when any error bit (fail, bad, eof) is set.


Example:
```
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ifstream fin("numbers.txt");
    
    if (!fin) {
        cerr << "Cannot open file\n";
        return 1;
    }

    int value;

    while (true) {
        fin >> value;
        
        if (fin.eof()) {
            cout << "Reached end of file\n";
            break;
        }
        if (fin.fail()) {
            cout << "Invalid data in file\n";
            fin.clear();          // repair stream
            fin.ignore(1000, '\n');
            continue;
        }
        
        cout << "Read: " << value << endl;
    }

    fin.close();
}
```

