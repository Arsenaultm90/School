MongoDB is a NoSQL document-based database.
Mongo stores ‘collections’ of ‘documents’
Database -> Collection(s) -> Document(s)
Mongo creates its own unique IDs for documents



Setting up MongoDB in project:
```
npm init -y

npm install mongodb
```

#### Start a MongoDB Server
For complete MongoDB installation instructions, see [the manual](https://www.mongodb.com/docs/manual/installation/).

1. Download the right MongoDB version from [MongoDB](https://www.mongodb.org/downloads)
2. Create a database directory (in this case under **/data**).
3. Install and start a `mongod` process.

```
mongod --dbpath=/data
```
You should see the **mongod** process start up and print some status information.

OR

BREW:
```
brew services start mongodb/brew/mongodb-community

Test:
mongo
mongosh
```


Connect to Database:
```
const { MongoClient } = require('mongodb');
// or as an es module:
// import { MongoClient } from 'mongodb'

// Connection URL
const url = 'mongodb://localhost:27017';
const client = new MongoClient(url);

// Database Name
const dbName = 'myProject';

async function main() {
  // Use connect method to connect to the server
  await client.connect();
  console.log('Connected successfully to server');
  const db = client.db(dbName);
  const collection = db.collection('documents');

  // the following code examples can be pasted here...

  return 'done.';
}

main()
  .then(console.log)
  .catch(console.error)
  .finally(() => client.close());
```


Run App:
```
node app.js
```



---
# Mongo Shell

Show all databases : `show dbs`
Use (or create) a database: `use myDB`
Show Collections: `show collections`
Insert a document: `myDB.users.insertOne({name: "Matt", age: 35})`
Find all documents: `myDB.users.find()`
Find with a condition: `myDB.users.find({name: "Matt"})`
Delete documents: `myDB.users.deleteOne({name: "Matt"})`
Drop a collection: `myDB.users.drop()`
Drop a database: `myDB.dropDatabase()`

How to quit shell: `exit` or `cmd + D`




