- All MCQ out of 72
- Cumulative, most important topics:
    - ER Models. We will be given an ER Diagram with 3 entity sets and relationships and a brief description of what the ER Model represents. Then we will have 10 questions about the ER Model.
    
	- SQL. We will be given a schema for a database represented as text. Example: Table1(column1 (PK), column2 (FK), column3), etc. And a description explaining the schema. There will be 10 questions about SQL related to this schema, some of them will be very tricky. Most of the questions will be determining which query is the correct query, but not all of them. (No relational algebra or TRC, but we should understand RA conceptually.)

	- The next question is 28 MCQ on the following topics, relatively simple:
		- Apps (tiers, connectivity, etc)
			- Normalization (1NF, 2NF, 3NF and functional dependencies)
			- Indexing (primary, secondary, cluster, B+ tree)
			- Files (How do we store data on the hard drive? How is it organized? Sorted, unsorted, etc.)
			- DBMS internal structure (parser, optimization)
		
	- The next question is worth 6 marks and is related to NoSQL:
		- MongoDB, SPARQL
		
	- Next question is related to graph databases, worth 8 marks. We will be given triples (subject, predicate, object) and asked 8 questions about this graph.
		- RDF
		
	- The last question is worth 9 marks and is specifically about MongoDB:
		- We will be given documents and asked 9 questions.
			- Many will be related to MongoDB queries, with a few general questions. Similar to the 5th assignment.



---
# ER Modelling

### **Entity Types**
- Strong vs weak entities
    - _Weak entities_: require owner entity + partial key + identifying relationship
- Composite attributes, multivalued attributes
    - Composite → broken down into subattributes
    - Multivalued → mapped as **separate table**

### **Relationships**
- **Cardinality constraints**: 1–1, 1–many, many–many
- **Participation constraints**: total vs partial
- **Identifying vs non-identifying relationships**
    - Identifying → dashed underline on weak entity
- **Degree of relationship**: binary, ternary


### **Keys in ER**
- Primary key = uniquely identifies entity
- In relationships:
    - _1–many_: place FK on the "many" side
    - _many–many_: create relationship table with 2 FKs
    - _1–1_: FK can go either side (depends on participation)


### **Mapping ER → Relational Schema**
You must know mapping rules cold:
- Entity → Table
- Composite attribute → flatten
- Multivalued → new table (PK includes the parent key)
- Weak entity → table with FK to owner + partial key
- Relationship:
    - 1–N → FK on N side
    - M–N → separate table
    - 1–1 → FK on one side
    - Ternary → separate table with 3 FKs



---
# SQL

#### **JOINs**
- INNER vs LEFT vs RIGHT
- NATURAL JOIN pitfalls (joins on _all_ same-named attributes)
- CROSS JOIN × Cartesian product

#### **Aggregates**
- `HAVING` filters groups
- `WHERE` filters rows _before_ grouping
- `COUNT(*)` includes NULLs, `COUNT(column)` does NOT

#### **Subqueries**
- IN vs EXISTS
- Scalar vs multi-row subqueries
- Correlated subqueries (executed per-row)

#### **NULL behavior**
- `NULL = NULL` → unknown
- `IS NULL` required to test nullness
- Aggregates ignore NULL except `COUNT(*)`

#### **Keys & FKs**
- A foreign key CAN be NULL
- PK can never be NULL
- Unique constraints allow one NULL (SQL standard)



---
# Tiered Architecture + Maps

### **Tier Models**
- **1-tier:** everything local (DB + UI + logic)
- **2-tier:** client/server
- **3-tier:** presentation → application server → DB server
- **n-tier:** microservices, distributed systems

### **Connection Models**
- **Connection pooling**
- **Stateless vs stateful servers**
- **Middle-tier responsibilities**: auth, business logic, validation



---
# **Normalization (1NF, 2NF, 3NF)**

#### **Functional Dependencies**
Be able to identify:
- Full FD: A → B
- Partial FD: (A, C) → B where A alone determines B
- Transitive FD: A → B and B → C ⇒ A → C

#### **1NF**
- No repeating groups
- No multivalued attributes
- Atomic values

#### **2NF**
- In 1NF
- No **partial dependency** on a composite key

#### **3NF**
- In 2NF
- No **transitive dependency**



---
# **Indexing (primary, secondary, clustered, B+ tree)**

#### **Primary index**
- Built on a **sorted** data file
- Based on the **primary key**
- File is ordered by this key

#### **Secondary index**
- Built on unsorted file or non-PK
- Can have duplicates
- Uses pointers to records

#### **Clustered index**
- File is physically ordered on index key
- Only **one** clustered index per table
- Massive speedup for range queries

#### **B+ trees**
Essential properties:
- Balanced tree
- All data keys stored in leaf nodes
- Linked leaves → efficient range search
- Height is very small (3–5 typically)



---
# File Storage & Organization

#### **How DBMS Stores Data on Disk**
1. **Blocks/Pages**
    - Smallest unit DB reads/writes (e.g., 4KB, 8KB).
2. **Tables are stored as files consisting of pages.**
3. **Records stored inside pages**, either:
    - Fixed length
    - Variable length (offset table used)

#### **File Organization Methods**
**1. Heap (Unordered)**
- Records inserted wherever there is space
- Fast inserts
- Slow search unless indexed

**2. Sorted File**
- Records stored in sorted order by key
- Fast binary search
- Very slow insertions (shifting pages)

**3. Hashing**
- Records placed using a hash function
- Fast equality search
- Terrible for range queries

#### **Record Formats**
- Fixed vs variable
- Slotted page format
- Pointers to free space

#### **Buffer Manager**
- Decides which pages stay in RAM
- Uses replacement policies (LRU, MRU)



---
# **DBMS Internal Structure**

#### **1. Parser**
- Checks SQL syntax
- Builds parse tree

#### **2. Query Optimizer**
- Chooses the best query plan
- Considers:
    - Join order
    - Index usage
    - Cost models (I/O vs CPU)

#### **3. Query Executor**
- Runs the chosen execution plan

#### **4. Storage Manager**
- Handles pages, records, file organization

#### **5. Transaction Manager**
- Logging
- Concurrency control
- Recovery


---
# NOSQL

#### **MongoDB Basics**
**Documents & Collections**
- JSON-like
- No schema
- Fields can vary
- Nested objects allowed

**Basic Query Operators**
- `$eq`, `$ne`, `$gt`, `$gte`, `$lt`, `$in`, `$nin`
- Logical: `$and`, `$or`, `$not`
- Array operators: `$elemMatch`, `$size`

**Projection :**
```
db.collection.find({}, {field: 1, _id: 0})
```

**Updates :**
```
$set, $inc, $push, $pull
```

Syntax :
```
db.collection.find({})
db.collection.findOne({})
db.collection.insertOne({})
db.collection.insertMany([{}])
db.collection.updateOne({})
db.collection.updateMany({})
db.collection.replaceOne({})
db.collection.deleteOne({})
db.collection.delterMany({})
db.collection.countDocuments()
db.collection.find().sort({ id: 1})  //ascending
db.collection.find().sort({ id: -1}) //descending
db.collection.drop()
db.dropDatabase()
```



**Aggregation Pipeline**
- `$match`
- `$group`
- `$project`
- `$lookup` (join)


#### **SPARQL Basics**
**RDF Terms**
- Subject
- Predicate
- Object

Triples define a graph of nodes with labelled edges.

**Key SPARQL Concepts**
- `SELECT` queries
- Pattern matching via triples
- `OPTIONAL`
- `FILTER`
- Prefixes
- `?var` used for variables

Example : 
```
SELECT ?name WHERE {
  ?x rdf:type :Person .
  ?x :name ?name .
}
```



---
# RDF (Resource Description Framework)

RDF EXAMPLE — WITH TRIPLES :
```
(Person1, type, Person)
(Person1, name, "Alice")
(Person1, worksAt, CompanyA)
(Person1, livesIn, CityX)

(Person2, type, Person)
(Person2, name, "Bob")
(Person2, worksAt, CompanyA)
(Person2, supervises, Person3)

(Person3, type, Person)
(Person3, name, "Carla")
(Person3, worksAt, CompanyB)

(CompanyA, locatedIn, CityX)
(CompanyB, locatedIn, CityY)
(CityX, neighborOf, CityY)
```

#### **What is the degree of a node?**

Degree = Number of edges connected to it
Example:
- `Person1` has outgoing edges: `type`, `name`, `worksAt`, `livesIn` → **degree 4**
- Incoming edges count too if asked (in-degree vs out-degree).


#### **Which nodes are connected / reachable from another node?**

Example:  
From `Person1`, what nodes are reachable using outgoing edges?
- Person
- "Alice"
- CompanyA
- CityX
- CityY (via CompanyA → CityX → neighborOf → CityY)
Sometimes reachability is only **one step**, sometimes **any number of hops**.


#### **Is there a path between two nodes?**

Example:  
Is there a path from `Person1` to `CompanyB`?
Steps:
- Person1 → livesIn → CityX
- CityX → neighborOf → CityY
- CompanyB is locatedIn CityY
→ Yes, there is a path (length = 3 edges).


#### **Identify all triples related to a node**

Example:  
Triples for Person3:
```
(Person3, type, Person)
(Person3, name, "Carla")
(Person3, worksAt, CompanyB)
(Person2, supervises, Person3)
```


#### **Which nodes belong to a class?**
Class membership comes from `(X, type, Y)` triples.

Example:  
All Persons are the subjects in triples of the form:
```
(?x, type, Person)
```
So the persons are:
- Person1
- Person2
- Person3


#### **Identify relationships (1-to-1, 1-to-many, etc.)**

Example:  
`worksAt`:
- Person1 → CompanyA
- Person2 → CompanyA
- Person3 → CompanyB

Thus:
- CompanyA has 2 people working at it
- CompanyB has 1  
    This is a **many-to-one** relationship (many persons → one company).


#### **Graph patterns / triangle detection**

Example:  
Do the cities form a triangle?

CityX neighborOf CityY  
(NO triple says CityY neighborOf CityX or CityY neighborOf CityZ, etc.)

So → **not a triangle**.


#### **Inference from simple predicate semantics**

(Not RDFS inference — just graph interpretation.)
Examples:

**Q: “Who lives in the same city as Alice works in?”**
Alice = Person1  
Alice worksAt → CompanyA  
CompanyA locatedIn → CityX

So:  
Which people live in CityX?
- Person1 (given)
- No others (Person2 livesIn not specified)

**Q: “Who works in a neighboring city to where Alice lives?”**
Alice livesIn CityX → neighborOf CityY  
Who worksAt something locatedIn CityY?
- CompanyB locatedIn CityY  
    → Person3 worksAt CompanyB

Answer: **Person3**


#### **Counting questions**

Examples:
- How many Person nodes? → 3
- How many companies? → 2
- How many edges with predicate `worksAt`? → 3
- How many nodes have at least one outgoing edge? → count subjects


#### **Identifying isolated nodes**

A node is isolated if it has:
- no incoming edges
- no outgoing edges