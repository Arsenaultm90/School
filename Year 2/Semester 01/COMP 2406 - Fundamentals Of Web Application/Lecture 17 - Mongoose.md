**Mongoose** is an **Object Data Modelling (ODM) library** for **MongoDB** in Node.js.

In simple terms:
- It lets you **define schemas** for your data
- It gives you a **model** that represents a MongoDB collection
- It allows **validation**, **hooks**, **query helpers**, and **relationship-like structures**
- It organizes your data similar to SQL tables, but flexible

MongoDB is schema-less — Mongoose _adds a schema layer on top_ for cleaner code and validation.


#### Why Use Mongoose?
1. **Schemas** → enforce structure on MongoDB documents
2. **Models** → high-level API for CRUD operations
3. **Built-in validation**
4. **Middleware (hooks)** → `pre`, `post` operations
5. **Helper functions** → `find`, `findOne`, `save`, `updateOne`, etc.
6. **Relationships** via `ref` and `populate()`
7. **Cleaner code + fewer errors**


**Connection** :
```
const mongoose = require("mongoose");

mongoose.connect("mongodb://127.0.0.1:27017/mydb")
  .then(() => console.log("Connected"))
  .catch(err => console.log(err));
```



---
# Schemas

A **Schema** defines the shape (structure) of documents in a collection.

```
const userSchema = new mongoose.Schema({
  username: { type: String, required: true },
  age: { type: Number, min: 0 },
  isAdmin: { type: Boolean, default: false },
  createdAt: { type: Date, default: Date.now }
});
```

#### Schema Features / Properties
1. **Type**
- `String`, `Number`, `Boolean`, `Date`, `Array`, `Buffer`, `ObjectId`

2. **Required**:
```
required: true
```

3. **Default:**
```
default: Date.now
```

4. **Validation rules**
- `min`, `max` for numbers
- `enum` for allowed strings
- `match` for regex
- custom validators

5. **Methods**
Add functions available ON DOCUMENTS.
```
userSchema.methods.sayHello = function() {
  console.log("Hello " + this.username);
};
```

6. **Statics**
Functions available on the MODEL itself.
```
userSchema.statics.findAdmins = function() {
  return this.find({ isAdmin: true });
};
```

7. **Virtuals**
Computed fields that are NOT stored in the database.
```
userSchema.virtual("isAdult").get(function() {
  return this.age >= 18;
});
```

8. **Middleware (Hooks)**
Runs before or after certain actions.
```
userSchema.pre("save", function(next) {
  console.log("About to save user...");
  next();
});
```



---
# Models

A **Model** is a constructor compiled from your schema.  
It represents a MongoDB **collection**.

```
const User = mongoose.model("User", userSchema);
```

Now you can use :
```
const user = new User({ username: "Matt", age: 21 });
await user.save();
```



---
# CRUD Operations

Create :
```
const user = new User({ username: "John", age: 30 });
await user.save();

// OR shortcut
await User.create({ username: "Anna", age: 22 });
```

Read :
```
await User.find();               // get all
await User.find({ age: { $gt: 20 }});
await User.findOne({ username: "John" });
await User.findById(id);
```

Update :
```
await User.updateOne({ username: "John" }, { age: 25 });

await User.findByIdAndUpdate(id, { age: 40 }, { new: true });
```

Delete :
```
await User.deleteOne({ username: "John" });
await User.findByIdAndDelete(id);
```



---
# Relationships + Populate

Mongoose simulates relations using `ObjectId` references.

Schema :
```
const postSchema = new mongoose.Schema({
  title: String,
  author: { type: mongoose.Schema.Types.ObjectId, ref: "User" }
});
```

Query w/ populate :
```
Post.find()
  .populate("author")
  .then(posts => console.log(posts));
```
This automatically fetches the author document.



---
# Syntax

Define Schema :
```
const schema = new mongoose.Schema({...});
```

Create Model :
```
const Model = mongoose.model("Name", schema);
```

Create Document :
```
const doc = new Model({...});
await doc.save();
```

Find Documents :
```
Model.find();
Model.findOne();
Model.findById();
```

Update Documents :
```
Model.updateOne();
Model.findByIdAndUpdate();
```

Delete Documents :
```
Model.deleteOne();
Model.findByIdAndDelete();
```


#### When to functions

|Task|Mongoose Function|
|---|---|
|Insert 1 doc|`new Model()` + `save()` OR `Model.create()`|
|Query many|`Model.find()`|
|Query one|`Model.findOne()`|
|Query by ID|`Model.findById()`|
|Update by ID|`Model.findByIdAndUpdate()`|
|Delete by ID|`Model.findByIdAndDelete()`|
|Add custom document method|`schema.methods`|
|Add static model method|`schema.statics`|
|Pre/post hooks|`schema.pre`, `schema.post`|
|Join-like query|`populate()`|
