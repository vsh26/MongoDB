# MongoDB CRUD Operations

## Create Operation Queries

- `db.collection.insertOne(<document>);` - Insert single document into a collection
- `db.collection.insertMany([<document1>, <document2>, ...]);` - Insert multiple documents 

## Read Operation Queries

- `db.collection.find(<query>, <projection>, <options>);` - General find syntax
- `db.collection.find();` - Fetch all documents from a collection
- `db.collection.find({});` -  Fetch all documents from a collection (same as above)
- `db.collection.find({qty: 20});` - Fetch all documents, where `qty` is `20`
- `db.collection.find({qty: {$gt: 20}});` - Fetch all documents, where `qty` is greater than `20`

Example:
```javascript
db.users.find({}, { name: 1, age: 1, _id: 0 })
// returns only name & age, excludes _id
```

### Common Query Operators

| Operator | Meaning      | Example                                            |
| -------- | ------------ | -------------------------------------------------- |
| `$eq`    | Equal        | `{ age: { $eq: 18 } }`                             |
| `$gt`    | Greater than | `{ age: { $gt: 18 } }`                             |
| `$lt`    | Less than    | `{ age: { $lt: 18 } }`                             |
| `$in`    | In array     | `{ name: { $in: ["Alice", "Bob"] } }`              |
| `$and`   | Logical AND  | `{ $and: [{ age: { $gt: 18 } }, { city: "NY" }] }` |
| `$or`    | Logical OR   | `{ $or: [{ city: "NY" }, { city: "LA" }] }`        |


## Update Operation Queries

- `db.collection.updateOne(<filter>, <update>, <options>);` - Update the first matching document
- `db.collection.updateMany(<filter>, <update>, <options>);` - Update all matching documents
- `db.collection.replaceOne(<filter>, <replacement>, <options>);` - Replace the entire document

Example:
```javascript
db.inventory.updateOne(
  { item: "book" },
  { $set: { qty: 25 } }
)
```

### Common Update Operators
| Operator | Meaning                | Example                          |
| -------- | ---------------------- | -------------------------------- |
| `$set`   | Set value of a field   | `{ $set: { age: 30 } }`          |
| `$inc`   | Increment value        | `{ $inc: { score: 5 } }`         |
| `$unset` | Remove a field         | `{ $unset: { middleName: "" } }` |
| `$push`  | Add item to array      | `{ $push: { tags: "new" } }`     |
| `$pull`  | Remove item from array | `{ $pull: { tags: "old" } }`     |


## Delete Operation Queries

- `db.collection.deleteOne(<filter>, <options>);` - Delete the first matching document
- `db.collection.deleteMany(<filter>, <options>);` - Delete all documents matching the filter
- `db.collection.deleteMany({});` - Deletes all documents in a collection

Refer:
- [MongoDB CRUD Operations](https://www.mongodb.com/docs/manual/crud/)
- [Query Operators](https://www.mongodb.com/docs/manual/reference/mql/query-predicates/#std-label-query-selectors)
