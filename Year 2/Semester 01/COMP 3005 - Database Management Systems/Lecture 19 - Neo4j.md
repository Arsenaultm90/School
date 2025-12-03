**Neo4j is the world’s most popular graph database**, designed specifically for highly connected data.

Its core features:
- **Nodes** = entities
- **Relationships** = directional edges connecting nodes
- **Properties** = key/value attributes
- **Labels** = group types of nodes (like tables in SQL)

Neo4j uses **Cypher**, a declarative query language (similar role to SQL but for graphs).


---
# Neo4j Data Model (Property Graph Model)

Neo4j stores a graph of:
**Nodes**
Represent entities:
```
(:Person {name: 'Alice', age: 21})
```

**Relationships**
Connect nodes and always have a **direction**:
```
(:Person)-[:KNOWS]->(:Person)
```

Relationships **can also store properties**:
```
(:Person)-[:FRIENDS_WITH {since: 2022}]->(:Person)
```

**Properties**
Key-value pairs, scalar values or arrays.

**Labels**
Node labels group nodes:
```
(:Student)
(:Course)
(:City)
```
A node can have **multiple labels**.


---
# Neo4j Architecture

1. **ACID Transactions**
Even though it's NoSQL, Neo4j provides ACID guarantees.

2. **Native Graph Storage**
Optimized for graph traversals (no joins).

3. **Index-Free Adjacency**
Each node stores references to its neighbors.  
→ Extremely fast traversals.

4. **Scalability**
Clustered deployments, read replicas, causal consistency.


---
# Cypher Query Language

Cypher uses ASCII-art patterns to describe graphs.

**Basic pattern:**
```
(node)-[relationship]->(node)
```

Examples:
```
MATCH (p:Person)-[:FRIENDS_WITH]->(q:Person)
```
Cypher commands are expressive and intuitive.


---
# Full CRUD Operations in Neo4J

Let’s use a simple graph:
```
(Alice)-[:KNOWS]->(Bob)
(Alice)-[:LIVES_IN]->(Ottawa)
(Bob)-[:LIVES_IN]->(Toronto)
```


#### CREATE (Insert)

**Create a node**:
```
CREATE (a:Person {name: 'Alice', age: 21})
```

**Create a relationship:**
```
MATCH (a:Person {name:'Alice'}), (b:Person {name:'Bob'})
CREATE (a)-[:KNOWS {since: 2022}]->(b)
```

**Create multiple nodes and relationships:**
```
CREATE
  (a:Person {name:'Alice'}),
  (b:Person {name:'Bob'}),
  (c:City {name:'Ottawa'}),
  (a)-[:LIVES_IN]->(c),
  (b)-[:KNOWS]->(a)
```


#### READ (Query)
Cypher uses the **MATCH** clause to search patterns.

Find all nodes with a label:
```
MATCH (p:Person)
RETURN p
```

Find nodes with properties:
```
MATCH (p:Person {name: 'Alice'})
RETURN p.name, p.age
```

Find relationships:
```
MATCH (a:Person)-[r:KNOWS]->(b:Person)
RETURN a.name, b.name, r.since
```

Pattern Matching:
```
MATCH (a:Person {name:'Alice'})-[:KNOWS]->(friends)
RETURN friends
```

Multiple Hops:
```
MATCH (a:Person {name: 'Alice'})-[:KNOWS*1..3]->(p)
RETURN p
```


#### UPDATE
Update node properties:
```
MATCH (p:Person {name:'Alice'})
SET p.age = 22
```


#### DELETE
Delete a node (only if it has no relationships):
```
MATCH (p:Person {name:'Bob'})
DELETE p

MATCH (:Person {name:'Alice'})-[r:KNOWS]->(:Person {name:'Bob'})
DELETE r

MATCH (p:Person {name:'Bob'})
DETACH DELETE p
```


---
# When to Use Neo4J

Neo4j is ideal for:
- Social networks
- Fraud detection
- Recommendation engines
- Knowledge graphs
- Network analysis
- Game design (skill trees, quest linking)
- Supply chain graphs

It excels when relationships are the core of the data.
