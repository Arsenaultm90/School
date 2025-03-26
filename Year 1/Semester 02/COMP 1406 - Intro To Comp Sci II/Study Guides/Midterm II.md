##### **Explain the concept of polymorphism**
Polymorphism is an object-oriented programming (OOP) concept that allows objects of different classes to be treated as objects of a common super class. It enables the same interface to be used for different data types. There are two types of polymorphism:

- **Compile-time polymorphism (Method Overloading)** – A class can have multiple methods with the same name but different parameters.
    
- **Runtime polymorphism (Method Overriding)** – A subclass can provide a specific implementation of a method that is already defined in its superclass.


##### **How can you determine how many valid ways an object can be typecast?**
The number of valid ways an object can be typecast depends on its position in the class hierarchy. An object can be:

- **Upcasted** to any of its superclasses or interfaces it implements.
- **Downcasted** to its subclass (only if the object is originally of that subclass type).


##### **a) Draw the most likely class hierarchy for the following classes: Arrow, Ball, BoardGame, Card, CardGame, Game, GameItem, Hero, MovingItem, Player, StationaryItem, Tree, Monster, Wall.**

```                  
Object
  |
  ├── GameItem                  (base class for all game items)
  |    ├── MovingItem           (extends GameItem)  
  |    |    ├── Ball            (extends MovingItem)
  |    |    └── Arrow           (extends MovingItem)
  |    ├── StationaryItem       (extends GameItem)
  |    |    └── Tree            (extends StationaryItem)
  |         └── Wall            (extends StationaryItem)
  |    └── Monster              (extends GameItem)
  |    └── Player               (extends GameItem)
  |         └── Hero
  |
  ├── Game                      (base class for games)
  |    ├── CardGame             (extends Game)
  |    |    └── Card            (extends CardGame)
  |    └── BoardGame            (extends Game)
```


b) Add a Playable interface and a Throwable interface to your Q.3 (a) diagram. The Playable interface includes a play() method, and the Throwable interface includes a
throw() method, both of which must be implemented by all classes that implement these
interfaces.



c) Recall that instances of any class can be typecast to Object because any class, by
default, is a subclass of the Object class. For each class in the logical hierarchy from your
answer to Q.3 (b), how many ways can you typecast it without causing an exception when
the code executes?



##### **What is the difference between an ADT and a data structure?**
- **Abstract Data Type (ADT)**: A theoretical model defining operations without specifying implementation (e.g., List, Stack, Queue).
    
- **Data Structure**: A concrete implementation of an ADT (e.g., ArrayList for List, LinkedList for Queue).


##### **What are the advantages of using a List/Queue/Stack/Set/Map ADT?**
- **List**: Ordered, indexed access.
- **Queue**: FIFO access, useful for scheduling.
- **Stack**: LIFO access, useful for backtracking.
- **Set**: Unique elements.
- **Map**: Key-value pairs, efficient lookups.


##### **When do you want to use an implementation of a List/Queue/Stack/Set/Map ADT in your code?**
- **List**: When order matters.
- **Queue**: When processing elements in order of arrival.
- **Stack**: When handling undo operations or recursion.
- **Set**: When uniqueness is required.
- **Map**: When key-value associations are needed.


##### **How does a List/Queue/Stack/Set/Map method work? Does it modify the data structure?Does it return a value?**
- Some modify the structure (e.g., `add()`, `remove()`).
- Some return values without modifying the structure (e.g., `get()`, `contains()`).


##### **What is the runtime used by the add/remove/search method of a List/Queue/Stack/Set/Map ADT implementation?**

| ADT   | Add  | Remove | Search |
| ----- | ---- | ------ | ------ |
| List  | O(n) | O(n)   | O(1)   |
| Queue | O(1) | O(1)   | O(n)   |
| Stack | O(1) | O(1)   | O(n)   |
| Set   | O(1) | O(1)   | O(1)   |
| Map   | O(1) | O(1)   | O(1)   |


##### **What is an exception in Java?**
An exception is an event that disrupts normal program execution.


##### **How does Java handle exceptions using try, catch, and finally?**
The 'try' block will attempt to execute the code. If an except occurs then it will skip to the catch block and execute the code within that block. It will then jump down to the 'finally' block where it will finish executing the within.

```
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
} finally {
    System.out.println("Execution completed.");
}

```


##### **What is the difference between checked and unchecked exceptions?**
- **Checked exceptions**: Must be handled (e.g., `IOException`).
- **Unchecked exceptions**: Runtime errors (e.g., `NullPointerException`).


##### **What is the purpose of the finally block in exception handling?**
Executes cleanup code regardless of whether an exception occurs.


##### **How does the throws keyword differ from throw in Java?**
- `throws`: Declares exceptions a method can throw.
- `throw`: Manually throws an exception.

 
##### **Explain with an example how we can have multiple catch blocks for a single try block.**
```
try {
    int arr[] = new int[5];
    arr[10] = 5;
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Index out of bounds");
} catch (Exception e) {
    System.out.println("General Exception");
}
```


##### **What happens if an exception is not caught in Java?**
The program crashes and displays a stack trace.


##### **What are the common Java input/output stream classes we covered in the lecture? How are they different from one another?**
- `FileInputStream` (byte-based file reading)
- `FileReader` (character-based file reading)
- `BufferedReader` (efficient line reading)
- `Scanner` (parsing input)


##### **How can you check if a file exists before reading it in Java?**
```
File file = new File("test.txt");
if (file.exists()) {
    System.out.println("File exists");
}
```


##### **What are the advantages of using each type of input/output stream class?**
- `BufferedReader`: Efficient reading.
- `FileInputStream`: Reads raw bytes.
- `Scanner`: Parses data easily.


##### **What is a GUI?**
A **Graphical User Interface (GUI)** allows users to interact with a program through visual elements instead of text commands.


##### **Why is it important to maintain a separation between the model, view, and controller in the MVC paradigm?**
- **Model**: Business logic.
- **View**: User interface.
- **Controller**: Manages user input.

MVC ensures **separation of concerns**, making code modular and maintainable.


##### **What is the role of a(n) model/view/controller/event handler within the MVC paradigm?**
- **Model**: Manages data.
- **View**: Displays data.
- **Controller**: Handles user input.
- **Event Handler**: Responds to user interactions.


##### **Which class does a view/controller class extend from?**
- **View** typically extends `JPanel` or `JFrame` (Swing).
- **Controller** does not necessarily extend a class but interacts with `ActionListener` for event handling.


##### **Comparable Interface**
```
public class Player implements Comparable<Player> {
    private String name;
    private int score;

    public Player(String name, int score) {
        this.name = name;
        this.score = score;
    }

    @Override
    public int compareTo(Player other) {
        return Integer.compare(this.score, other.score);
    }
}
```


##### Serializable Interface
The `Serializable` interface in Java is used when you want to **save an object to a file**, **send it over a network**, or **store it in a database**. It allows objects to be converted into a **byte stream**, which can later be reconstructed (deserialized) back into an object.

**Use cases:**
    - Saving game progress
    - Sending objects over a network (e.g., multiplayer games)
    - Storing object states in a file

**Define Player Class**
```
import java.io.Serializable;

public class Player implements Serializable {
    private static final long serialVersionUID = 1L; // Helps with version control
    private String name;
    private int score;

    public Player(String name, int score) {
        this.name = name;
        this.score = score;
    }

    @Override
    public String toString() {
        return "Player{name='" + name + "', score=" + score + "}";
    }
}
```

`serialVersionUID` is optional but **prevents compatibility issues** when modifying the class.


**Serialize(Save Object)**
```
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;

public class SavePlayer {
    public static void main(String[] args) {
        Player player = new Player("Alice", 100);

        try (FileOutputStream fileOut = new FileOutputStream("player.dat");
        ObjectOutputStream out = new ObjectOutputStream(fileOut)) {
            out.writeObject(player); // Save the object
            System.out.println("Player object saved!");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

`ObjectOutputStream` writes the object as a **byte stream** to a file.


**Deserialize(Load Object)**
```
import java.io.FileInputStream;
import java.io.IOException;
import java.io.ObjectInputStream;

public class LoadPlayer {
    public static void main(String[] args) {
        try (FileInputStream fileIn = new FileInputStream("player.dat");
        ObjectInputStream in = new ObjectInputStream(fileIn)) {
            Player loadedPlayer = (Player) in.readObject(); // Load the object
            System.out.println("Loaded Player: " + loadedPlayer);
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
```

`ObjectInputStream` reads the object **back into memory**.


#### **Understanding equals() and hashCode() in Java**
The `equals()` and `hashCode()` methods are **crucial** for object comparison and data structures like `HashMap`, `HashSet`, and `HashTable`. They determine whether two objects are **logically equal** and ensure **efficient storage and retrieval** in collections.

##### equals() Method
By default, `equals()` in `Object` **compares memory addresses** (i.e., `==`).  
We override it to **compare actual field values**.

```
class Player {
    String name;
    int score;

    public Player(String name, int score) {
        this.name = name;
        this.score = score;
    }
}

public class Main {
    public static void main(String[] args) {
        Player p1 = new Player("Alice", 100);
        Player p2 = new Player("Alice", 100);

        System.out.println(p1.equals(p2)); // false (compares memory locations)
    }
}

```

Even though `p1` and `p2` have **the same values**, `equals()` returns `false` because **we haven't overridden it**.


##### **Overriding equals() Properly**
We should override `equals()` to **compare actual values** instead of memory addresses.

```
class Player {
    String name;
    int score;

    public Player(String name, int score) {
        this.name = name;
        this.score = score;
    }

    @Override
    public boolean equals(Object o) {
	    if (o instanceof Student student) { // No need to manually cast
	        return id == student.id && Objects.equals(name, student.name);
	    }
	    return false;
    }
}

public class Main {
    public static void main(String[] args) {
        Player p1 = new Player("Alice", 100);
        Player p2 = new Player("Alice", 100);

        System.out.println(p1.equals(p2)); // true (compares values)
    }
}

```

- First, check if `this == obj` (same reference).
- Then, check `null` and **class type**.
- Finally, compare the **actual field values**.


#### **hashCode() Method**
`hashCode()` returns an `int` that **identifies the object in hash-based collections** like `HashMap` and `HashSet`.  

If two objects are **equal (`equals()` returns true)**, they **must have the same `hashCode()`**.

##### **Overriding `hashCode()`**
Use `Objects.hash()` or a simple formula:
```
import java.util.Objects;

class Player {
    String name;
    int score;

    public Player(String name, int score) {
        this.name = name;
        this.score = score;
    }

    @Override
    public boolean equals(Object obj) {
	    if (o instanceof Student student) { // No need to manually cast
	        return id == student.id && Objects.equals(name, student.name);
	    }
	    return false;
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, score); // Uses Java's built-in hashing
    }
}

public class Main {
    public static void main(String[] args) {
        Player p1 = new Player("Alice", 100);
        Player p2 = new Player("Alice", 100);

        System.out.println(p1.hashCode()); // Same hash for equal objects
        System.out.println(p2.hashCode()); // Same hash for equal objects
    }
}

```

##### **Why Is hashCode() Important?**
In **hash-based collections**:
- If `hashCode()` **is different**, objects are stored in **different buckets**.
- If `hashCode()` **is the same**, Java checks `equals()` to **resolve collisions**.


##### **Using equals() and hashCode() in a HashSet**
Without `hashCode()`, Java might **store duplicates** in a `HashSet`.

```
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {
        HashSet<Player> players = new HashSet<>();
        players.add(new Player("Alice", 100));
        players.add(new Player("Alice", 100));

        System.out.println(players.size()); // 1 (since hashCode & equals are overridden)
    }
}

```


| Method     | Purpose                                                                                         |
| ---------- | ----------------------------------------------------------------------------------------------- |
| equals()   | Compares two objects for logical equality (based on field values).                              |
| hashCode() | Generates a unique integer for the object, ensuring efficient lookup in hash-based collections. |
| Rule       | If `equals()` returns `true`, `hashCode()` **must be the same**.                                |

- Whenever it is invoked on the same object more than once during an execution of a Java application, _hashCode()_ must consistently return the same value, provided no information used in equals comparisons on the object is modified. This value doesn’t need to stay consistent from one execution of an application to another execution of the same application.

- If two objects are equal according to the _equals(Object)_ method, calling the _hashCode()_ method on each of the two objects must produce the same value.

- If two objects are unequal according to the [_equals(java.lang.Object)_](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/Objects.html#equals\(java.lang.Object,java.lang.Object\)) method, calling the _hashCode_ method on each of the two objects doesn’t need to produce distinct integer results. However, developers should be aware that producing distinct integer results for unequal objects improves the performance of hash tables.