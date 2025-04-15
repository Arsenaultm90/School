(Chapters 10, 11)

#### Data Streams in Java
Java provides a comprehensive framework for handling data streams, which allow you to read and write data sequentially. Here's an overview of how streams work in Java:

#### Basic Stream Concepts
Java organizes its I/O operations around streams, which represent sequences of data. There are two primary types:

1. **Byte Streams** - Work with binary data (8-bit bytes)
2. **Character Streams** - Work with text data (Unicode characters)


---
## File I/O Streams

#### Reading from Files

```
// Byte stream approach
try (FileInputStream fis = new FileInputStream("data.bin")) {
    int byteData;
    while ((byteData = fis.read()) != -1) {
        // Process each byte
    }
}

// Character stream approach
try (FileReader reader = new FileReader("text.txt")) {
    int charData;
    while ((charData = reader.read()) != -1) {
        // Process each character
    }
}

// Buffered reading for better performance
try (BufferedReader br = new BufferedReader(new FileReader("text.txt"))) {
    String line;
    while ((line = br.readLine()) != null) {
        // Process each line
    }
}
```


#### Writing to Files

```
// Byte stream approach
try (FileOutputStream fos = new FileOutputStream("output.bin")) {
    byte[] data = {65, 66, 67, 68}; // ABCD in ASCII
    fos.write(data);
}

// Character stream approach
try (FileWriter writer = new FileWriter("output.txt")) {
    writer.write("Hello, World!");
}

// Buffered writing for better performance
try (BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"))) {
    bw.write("Hello, World!");
    bw.newLine(); // Platform-independent newline
    bw.write("Another line");
}
```


---
## Object Serialization

Java allows storing and loading complete objects through serialization:

#### Storing Objects in Files

```
// Class must implement Serializable
class Person implements Serializable {
    private static final long serialVersionUID = 1L; // For version control
    private String name;
    private int age;
    
    // Constructor, getters, setters...
}

// Saving objects
try (ObjectOutputStream oos = new ObjectOutputStream(
        new FileOutputStream("people.dat"))) {
    Person person = new Person("John", 30);
    oos.writeObject(person);
}
```


#### Loading Objects from Files

```
try (ObjectInputStream ois = new ObjectInputStream(
        new FileInputStream("people.dat"))) {
    Person person = (Person) ois.readObject();
    // Use restored object
} catch (ClassNotFoundException e) {
    // Handle case where class definition can't be found
}
```


---
## Modern Approaches (Java NIO)

Java NIO (New I/O) introduced since Java 1.4 provides additional capabilities:

```
// Reading all bytes from a file
byte[] allBytes = Files.readAllBytes(Paths.get("data.bin"));

// Reading all lines from a text file
List<String> lines = Files.readAllLines(Paths.get("text.txt"));

// Writing text to a file
Files.write(Paths.get("output.txt"), 
            Arrays.asList("Line 1", "Line 2"), 
            StandardCharsets.UTF_8);
```
