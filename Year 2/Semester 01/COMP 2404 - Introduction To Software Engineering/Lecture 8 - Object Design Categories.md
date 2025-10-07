#### Overview 

In object-oriented programming, we aim for **modular design**. One way to achieve modularity is to **group objects into categories**.

- **What are object design categories?**
    - A method for organizing objects based on their roles in a system.
    - Most objects fall into one of these categories (sometimes more than one in smaller programs).
    - Each category has a **specific responsibility**.

- **Why use categories?**
    - Helps clarify what each class is supposed to do.
    - Encourages **single responsibility**: each class should serve one main purpose.
    - Improves **reusability** and **maintainability**.
    - Narrowing scope makes it easier to think about and design each class.


---
#### Object Categories

The four main object categories we use are:
1. **Entity Objects**
2. **Control Objects**
3. **Boundary Objects** (also called _View_ or _User Interface (UI) Objects_)
4. **Collection Objects**

##### Entity Objects
**Definition:**
- Represent **real-world objects** or **information the system tracks**.
- Typically store **persistent data** (saved between program sessions).

**Characteristics:**
- Contain **data** in member variables.
- Contain small, **entity-specific logic** (not whole-program logic).
- Usually simple in structure.

**Examples:**
- `Student`, `Instructor`, `Course`, `Book`, `BankAccount`.
- A `Student` might have attributes like `name`, `id`, and `gpa`, and functions like `lessThan(otherStudent)` for comparison.

**Key point:**
- Entity objects model **“things”** in the system, not program flow.


##### Control Objects
**Definition:**
- Responsible for **program flow** and **coordinating interactions** between other classes.
- Decide _which_ objects talk to each other and _when_.

**Characteristics:**
- Often manage **high-level interactions**.
- Typical OO main function:
```
int main() {
    Controller c;
    c.run();
}
```
- Here, `Controller` is a **top-level control object**.

**Examples:**
- `GameController` (manages the state of a game).
- `RegistrationManager` (coordinates between `Student` and `Course` classes).

**Key point:**
- Control objects handle **logic and flow**, but usually do not store persistent data.


##### Boundary Objects (View/UI Objects)

**Definition:**
- Sit at the **interface between the system and an external actor** (user, external system, or library).
- Present data from entities to the user and accept input from the user.

**Characteristics:**
- Handle input/output (e.g., text prompts, GUI forms, API endpoints).
- Do **not** contain major business logic.
- Translate between user language and system language.

**Examples:**
- `LoginScreen`, `MainMenu`, `WebForm`, `APIRequestHandler`.

**Key point:**
- Boundary objects are all about **communication at the edges of the system**.


##### Collection Objects
**Definition:**
- Special objects that store and manage **groups of entities**.

**Characteristics:**
- Encapsulate data structures (e.g., arrays, lists, maps).
- Provide operations for adding, removing, searching, or sorting elements.
- Often hold entity objects for easy access.

**Examples:**
- `StudentList` (manages multiple `Student` objects).
- `CourseCatalog` (holds all available courses).
- `Inventory` (in a game, stores all items a player owns).

**Key point:**
- Collections are about **organizing and accessing groups of entities efficiently**.


**Example: Student Registration System**
- **Entity Objects:** `Student`, `Instructor`, `Course`.
- **Collection Objects:** `CourseCatalog`, `StudentList`.
- **Control Objects:** `RegistrationManager` (coordinates course enrollment).
- **Boundary Objects:** `RegistrationUI` (displays available courses, accepts student input).

Flow:
1. The **boundary object** (`RegistrationUI`) asks the student which course they want.
2. The **control object** (`RegistrationManager`) checks if the course exists.
3. The **collection object** (`CourseCatalog`) is searched for the course.
4. If found, the student (`Entity`) is linked to the course (`Entity`).


---
#### Summary

- **Entity objects**: Represent real-world things and store persistent data.
- **Control objects**: Manage flow, coordinate between other classes.
- **Boundary objects**: Handle communication with users/external systems.
- **Collection objects**: Manage groups of entities.

**Design Principles:**
- Each class should have a **single responsibility**.
- Categorizing classes makes systems easier to design, understand, and extend.