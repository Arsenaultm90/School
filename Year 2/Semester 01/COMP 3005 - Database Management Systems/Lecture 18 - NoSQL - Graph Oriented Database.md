Graph databases are a type of NoSQL database built to store and query **highly connected data**.

Data is modeled as:
- **Nodes** (entities)
- **Edges** (relationships)
- **Properties** (attributes on nodes/edges)

Unlike relational DBMSs (tables + joins), graph DBs store connections **directly**.  
This makes them far better for:
- Social networks
- Recommendation systems
- Fraud detection
- Knowledge graphs
- Semantic web

Two major categories of graph databases exist:
1. **Property Graph Model**
Used by Neo4j, Amazon Neptune (also supports RDF), ArangoDB.
Structure:
- Nodes (with labels and properties)
- Edges (with types and properties)

Query language: **Cypher**

2. **RDF Graph Model (Semantic Web Model)**
Used by:
- Apache Jena
- Virtuoso
- Stardog
- Blazegraph
- Amazon Neptune (supports RDF)

Structure:
- Everything is stored as **triples** (subject, predicate, object)

Query language: **SPARQL** (pronounced “sparkle”).


---
# RDF – Resource Description Framework

RDF is a **data model for describing information on the web** using **triples**.

A triple is:
```
Subject   Predicate   Object
```

Example:
```
:Alice     :knows      :Bob
:Alice     :age        22
:Bob       :livesIn    :Ottawa
```

This forms a **graph**:
![[Pasted image 20251125085350.png|500]]

#### RDF Graph Characteristics
- **Subject** and **Predicate** are always URIs (unique identifiers)
    
- **Object** can be:
    - URI (another entity)
    - Literal (“Ottawa”, 22, etc.)

RDF graphs can be serialized in multiple formats:
- Turtle (.ttl)
- RDF/XML
- N-Triples
- JSON-LD

Example (Turtle format):
```
@prefix ex: <http://example.com/> .

ex:Alice ex:knows ex:Bob .
ex:Alice ex:age 22 .
ex:Bob   ex:livesIn ex:Ottawa .



```

Example Query:
```
PREFIX ex: <http://example.com/>

SELECT ?name ?title
WHERE {
    ?student ex:name ?name .
    ?student ex:takesCourse ?course .
    ?course  ex:title ?title .
}
```


#### Why RDF Exists
RDF was created for the **Semantic Web**, where:
- Machines can understand data semantics,
- Different organizations publish data using common vocabularies,
- Data integrates naturally because URIs ensure global uniqueness.


---
# SPARQL – The Query Language for RDF

SPARQL is to RDF what SQL is to relational databases.

#### Key Features:
- Graph pattern matching
- Optional matches
- Filters
- Aggregation
- Path expressions
- Federated queries (query remote RDF endpoints)

#### SPARQL Basic Query Structure
A SPARQL SELECT query:
```
PREFIX ex: <http://example.com/>

SELECT ?name
WHERE {
    ?person ex:age ?age .
    FILTER (?age > 20)
}
```
SPARQL looks for all triples matching the patterns.


#### Why Use RDF + SPARQL Instead of SQL?
RDF excels when:
1. Data is **highly connected**
- Social networks
- Knowledge graphs
- Recommendations
- Linked data

2. Schema changes frequently
RDF doesn’t require rigid schema tables.

3. You need **semantic meaning**
Using shared vocabularies (FOAF, schema.org, DBpedia).

4. You want to merge datasets from different organizations
RDF is globally unique because everything uses URIs.


#### Strengths of RDF Graph Databases
**Flexible schema**
Add new relationships anytime without altering tables.

**Excellent for relationship-heavy data**
No JOIN cost; relationships are stored as edges.

**Very expressive query language**
SPARQL supports pattern matching, optional matches, graph traversal.

**Global identifiers (URIs)**
Perfect for linking data across organizations.


#### Limitations of RDF Graph Databases
- Not ideal for **transaction-heavy** systems
- Slower for simple key-value or document use cases
- Harder to model entities with many attributes
- More complex than SQL for beginners

|Feature|RDF + SPARQL|Property Graph (Neo4j)|
|---|---|---|
|Structure|Triples (subject-predicate-object)|Nodes + edges + properties|
|Query Language|SPARQL|Cypher|
|Best Use|Semantic web, linked data|Operational graph queries (social networks, recommendations)|
|Identifiers|URIs|Labels/IDs|
|Schema|Very flexible|Flexible but structured|
|Vocabulary|Strong shared ontologies|No built-in ontology system|
