#### **What is NoSQL?**

**NoSQL (Not Only SQL)** refers to a family of database systems built to handle:
- Very large-scale data    
- High velocity of reads/writes
- Flexible, evolving data structures (no fixed schema)
- Distributed, horizontally scalable systems

NoSQL databases emerged to overcome limitations of traditional relational DBMSs when handling:
- Big Data
- Real-time web apps
- Rapid structure changes
- High-availability distributed systems (e.g., social media, IoT, gaming)

#### **Why NoSQL Exists (Key Drivers)**
1. **Scalability**
- SQL: vertical scaling (bigger server)
- NoSQL: horizontal scaling (add more servers)

2. **Flexible Schema**
- SQL: schema must be defined up-front
- NoSQL: schema-less; fields can vary across records

3. **High performance**
Designed for very fast writes/reads at scale.

4. **Handling unstructured data**
JSON, logs, user activity, sensor data, etc.

5. **Distributed architecture**
Replication, sharding, fault tolerance built-in.


#### **Categories of NoSQL Databases**

**1. Document Stores (MongoDB, CouchDB)**
Store data as **documents** (JSON-like).
- Flexible schema
- Ideal for hierarchical data
- Most widely used NoSQL type

**2. Key-Value Stores (Redis, DynamoDB)**
- Fastest type
- Simple key → value lookup
- Used for caching, sessions, counters

**3. Column-Family Stores (Cassandra, HBase)**
- Data stored in column families
- Very high write throughput
- Used by Facebook, Netflix, etc.


**4. Graph Databases (Neo4j, ArangoDB)**
- Nodes + edges
- Handle highly connected data
- Used for social graphs, recommendation engines



---
# **MongoDB**

MongoDB stores data in **BSON documents** (Binary JSON).  
Think of it as storing JSON objects with powerful indexing and querying.

#### Basic structure hierarchy:
- **Database**
    - **Collection** (like a table)
        - **Documents** (like rows)
            - **Fields** (like columns)

Unlike SQL, documents **can have different fields**, and nested objects are allowed.


#### **MongoDB Architecture**

1. **Document Model**
Documents look like JSON:
```
{
  "name": "Alice",
  "age": 21,
  "courses": ["CS2001", "MATH1007"],
  "address": {
    "city": "Ottawa",
    "postal": "K1A0B1"
  }
}
```
Documents in the same collection do **not** need identical fields.

2. **Sharding** (Horizontal Scaling)
MongoDB automatically spreads data across multiple servers.

3. **Replication**
ReplicaSets = automatic failover + redundancy  
(Primary + Secondary nodes)

4. **Indexes**
Similar to SQL:
- Single field
- Compound
- Text
- Geospatial  
    All supported.


#### **CRUD Operations in MongoDB**

MongoDB uses a JavaScript-like shell.

**INSERT**
```
db.students.insertOne({
  name: "Matt",
  age: 22,
  major: "Computer Science",
  gpa: 3.9
})
```

**READ/FIND**
```
db.students.find({ gpa: { $gt: 3.5 } })
```

Query w/ Projections
```
db.students.find(
  { major: "Computer Science" },
  { name: 1, gpa: 1, _id: 0 }
)
```

**UPDATE**
```
db.students.updateOne(
  { name: "Matt" },
  { $set: { gpa: 4.0 } }
)
```

**DELETE**
```
db.students.deleteOne({ name: "Matt" })
```


#### **MongoDB Query Operators**
**Comparison:**
- `$gt`, `$lt`, `$gte`, `$lte`, `$eq`, `$ne`

**Logical:**
- `$and`, `$or`, `$not`, `$nor`

**Array:**
- `$in`, `$all`, `$elemMatch`

**Update modifiers:**
- `$set`
- `$inc`
- `$push`, `$pull`
- `$addToSet`


#### **Indexing Example**
Create an index on `gpa`:
```
db.students.createIndex({ gpa: 1 })
```

Create a compound index:
```
db.students.createIndex({ major: 1, gpa: -1 })
```


#### **When to Use MongoDB**
Use MongoDB if you need:
- Flexible schemas that change often
- Large-scale data (millions–billions of documents)
- High-speed insert/write operations
- Horizontal scaling
- Real-time analytics
- Nested/hierarchical data

**Examples:**
- E-commerce catalog
- Social media posts
- Logging systems
- User profiles
- Content management
- IoT/stream data

#### **When NOT to Use MongoDB**

Avoid when:
- You need many complex JOINs
- Strong ACID transactions are critical
- Schema consistency is important
- Data is highly relational (e.g., banking, ERP)

