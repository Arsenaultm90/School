## Software Engineering
**What is it?** Software engineering is the application of systematic, disciplined, and measurable approaches to the development, operation, and maintenance of software. It applies engineering principles to software creation.

**Why is it necessary?**
- Software systems are complex — without structure, they become unmaintainable
- Reduces bugs, cost overruns, and project failures
- Ensures the final product actually meets the client's needs
- Makes large team collaboration possible
  

---
## Build Models

**What is a model?** A **virtual representation** of the system you're going to build, like a blueprint before constructing a building.

**Why build models?**
- Get a clearer picture of _how_ to build the real system
- Clarify details and requirements so you build the **right** thing
- Catch design mistakes early (much cheaper to fix on paper than in code)

**Traceability** — the ability to track requirements through the _entire_ development process.

**Why traceability matters:**
- Better for maintenance
- Tells you which parts of the system are related
- Makes it clear what needs to change when something changes


---
## Software Development Life Cycle (SDLC)

The phases in order, and their key work products:

|Phase|Work Product|
|---|---|
|**Requirements Elicitation**|Use cases, requirements list|
|**Analysis**|Refined use cases, class diagrams, sequence diagrams|
|**High-Level System Design**|Architecture diagrams, subsystem breakdown|
|**Detailed Object Design**|Detailed class diagrams, contracts|
|**Implementation**|Source code|
|**Testing / QA**|Test cases, bug reports, test results|
|**Deployment & Maintenance**|Deployed system, patches, updates|


---
## Models in Requirements Analysis

There are **three types of models**, each answering a different question:

|Model|What it captures|UML Diagrams|
|---|---|---|
|**Functional Model**|_What_ the system does|Use cases, requirements|
|**Dynamic Model**|_When/how_ the system behaves over time|State machines, sequence diagrams, activity diagrams|
|**Object Model**|_What_ the system is made of|Class diagrams, data dictionaries|

Think of them as: **what it does → how it behaves → what it's made of.**


---
## Requirements Elicitation

**Goal:** Figure out what the client actually wants.

**Two types of requirements:**
- **Functional** — what the system _does_ (e.g., "user can log in")
- **Non-functional** — qualities the system must have, across **9 categories** (e.g., performance, security, usability, reliability, etc.)

**Scenarios & Use Cases:**
- **Scenarios** are concrete examples of how a user interacts with the system
- **Use cases** generalize those scenarios

**Use Case concepts to know:**
- **High-level vs. Detailed** — high-level is a brief summary; detailed includes full flow, preconditions, postconditions, exceptions
- **Actors** — end users _or_ external systems that interact with the system
- **System boundary** — defines what's inside vs. outside the system
- **Actor relationships:** _initiate_ (starts the use case) vs. _participate_ (is involved but doesn't start it)
- **Use case relationships:**
    - **«include»** — one use case always calls another (required dependency)
    - **«extend»** — one use case optionally extends another (conditional behaviour)
    - **Inheritance** — a child use case inherits from a parent use case
- **UML Use Case Diagrams** + **Use Case Table Descriptions** are the deliverables


---
