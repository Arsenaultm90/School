
# Analysis Object Model

The **analysis object model** is a **conceptual representation of the problem domain** using objects.

#### Categories of objects
**Entity objects**
	Application domain objects
	Persistent information tracked by the system
**Boundary objects**
	Used for interactions between actors and the system
**Control objects**
	In charge of realizing use cases

Example: Online Store
	From requirements like:
> 	“Users can place orders and pay for products”

You identify objects:
- User
- Order
- Product
- Payment

With attributes:
- User: `userID`, `email`
- Order: `orderID`, `date`
- Product: `price`, `name`

And relationships:
- User **places** Order
- Order **contains** Product



---
# Generalization and Specialization

This is classic **inheritance**, but at the **analysis level**, not code yet.

### Generalization
- A **more general** concept
- Captures shared attributes and behavior

### Specialization
- A **more specific** version
- Adds or modifies behavior

Key relationship:
> **“is-a” relationship**

**Example :**
General class :
- `User`

Specialized classes :
- `Admin`
- `Customer`
- `Guest`

Rules:
- Admin **is a** User
- Customer **is a** User
- Guest **is a** User

**Why this matters in analysis**
- Reduces duplication
- Clarifies shared vs unique responsibilities
- Sets up clean OOP design later

#### Analysis vs Design
- **Analysis**: identifies relationships
- **Design**: decides implementation details (methods, access modifiers, etc.)



---
# Dynamic Model

The **dynamic model** describes **how the system behaves over time**.

Key question:
> _What happens when users interact with the system?_

Unlike the object model (which is static), the dynamic model focuses on:
- Events
- States
- Transitions
- Interactions

#### Common Dynamic Models
1. Sequence Diagrams
	Show **interaction order** between objects.

Example:
1. User clicks “Buy”
2. Order is created
3. Payment is processed
4. Confirmation is sent

> Who talks to whom, and in what order?

#### 2. State Diagrams
Show how an object **changes state** over time.

Example: Order
- Created
- Paid
- Shipped
- Delivered
- Cancelled

> What states can this object be in, and how does it move between them?


### Why Dynamic Models Matter
- Catch missing logic early
- Reveal invalid states
- Clarify complex workflows
- Prevent contradictory requirements



---
# Summary

- **Analysis Object Model**: A conceptual model of domain objects, their attributes, and relationships.
- **Generalization**: Extracting common features into a more general class.
- **Specialization**: Creating more specific classes from a general one.
- **Dynamic Model**: A representation of system behaviour over time using interactions and state changes.
