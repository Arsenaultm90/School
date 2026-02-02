#### Unified Modelling Language
A tool for expressing system models


#### Models and notations
Functional model
	use case diagrams
Dynamic model
	sequence diagrams
	state machine diagrams
	activity diagrams
Object model
	class diagrams



#### Use Case Diagrams
==[Unified Modeling Language](https://www.google.com/search?client=firefox-b-d&q=Unified+Modeling+Language&mstk=AUtExfCL9d29oW89LYGRfCS5cZ3_7dr3sSUjXrtNHMFhsUXuKSRWvEHsBupsHwuD4wLEAe4RZyzk_U1R3R450pgt1tHIy6vBNj-OeO0j1S4O27zhlckUcgEe0lwb2Y6fSY6TLeBuUgQja97TfhsciIRpTENOUhPdLip5BqFuhLTdV1f3unEBpcYMp_V7hfWQb2ZpuZizBN4UpPU_6VtnHf_U5HPXJe9PYO4cHS_1sCEaBX37ZTd80Kf8PrN_WNXV7KEnqjx5fKG731ScnuEE9P8Sc0RR&csui=3&ved=2ahUKEwjm-6br0JySAxW6HjQIHWTVD8gQgK4QegYIAQgAEBE) (UML) diagrams that visually represent how users (actors) interact with a system to achieve specific goals==, showing the system's functionalities (use cases) and their relationships in a high-level, easy-to-understand format for requirements analysis and communication.

![[Pasted image 20260121072935.png|300]]


#### Class Diagrams
A **UML (Unified Modeling Language) class diagram** visually represents the **static structure** of an object-oriented system. It shows **classes**, their **attributes**, **methods**, and the **relationships** between them.

**Core components:**
- **Class**: Represented as a rectangle divided into three sections:
    - Class name
    - Attributes (fields)
    - Methods (operations)
- **Visibility modifiers**:
    - `+` public
    - `-` private
    - `#` protected
- **Relationships**:
    - **Association** – general connection between classes
    - **Aggregation** – “has-a” relationship (weak ownership)
    - **Composition** – strong ownership; lifecycle dependent
    - **Inheritance (Generalization)** – “is-a” relationship
    - **Dependency** – temporary usage relationship
- **Multiplicity**: Indicates how many instances participate (e.g., `1`, `0..*`)



#### UML Object Diagrams
A UML object diagram represents a snapshot of a system at a specific moment in time, showing actual object instances, their current attribute values, and the links between them.

**Core components:**
- **Objects**: Instances of classes, written as `objectName:ClassName` (often underlined)
- **Attribute values**: Concrete values assigned at that moment
- **Links**: Runtime connections between objects (instances of associations)
- **Multiplicity**: Implied by the number of objects shown, not explicitly labeled

![[Screenshot 2026-01-21 at 7.38.04 AM.png|300]]



