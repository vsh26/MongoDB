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

| Operator  | Description                      | Example Query                                                               |
| --------- | -------------------------------- | --------------------------------------------------------------------------- |
| `$eq`     | Equal to                         | `{ age: { $eq: 18 } }` → matches docs where `age` = 18                      |
| `$ne`     | Not equal to                     | `{ status: { $ne: "active" } }` → matches docs where `status` ≠ "active"    |
| `$gt`     | Greater than                     | `{ qty: { $gt: 20 } }` → matches docs where `qty` > 20                      |
| `$gte`    | Greater than or equal to         | `{ qty: { $gte: 20 } }` → matches docs where `qty` ≥ 20                     |
| `$lt`     | Less than                        | `{ qty: { $lt: 20 } }` → matches docs where `qty` < 20                      |
| `$lte`    | Less than or equal to            | `{ qty: { $lte: 20 } }` → matches docs where `qty` ≤ 20                     |
| `$in`     | Matches any value in an array    | `{ city: { $in: ["NY", "LA"] } }` → matches docs where `city` is NY or LA   |
| `$nin`    | Not in array                     | `{ city: { $nin: ["NY", "LA"] } }` → excludes docs where `city` is NY or LA |
| `$and`    | Logical AND                      | `{ $and: [ { age: { $gt: 18 } }, { city: "NY" } ] }`                        |
| `$or`     | Logical OR                       | `{ $or: [ { city: "NY" }, { city: "LA" } ] }`                               |
| `$not`    | Negates query condition          | `{ age: { $not: { $gt: 30 } } }` → matches docs where `age` ≤ 30            |
| `$exists` | Field existence check            | `{ phone: { $exists: true } }` → matches docs where `phone` field exists    |
| `$regex`  | Pattern matching (like SQL LIKE) | `{ name: { $regex: /^A/ } }` → matches docs where `name` starts with A      |
| `$all`       | Matches arrays that contain **all** specified elements                  | `{ tags: { $all: ["red", "round"] } }` → matches docs where `tags` has both `"red"` and `"round"`                                                    |
| `$size`      | Matches arrays with the specified length                                | `{ tags: { $size: 3 } }` → matches docs where `tags` array has exactly 3 elements                                                                    |
| `$elemMatch` | Matches if **at least one array element** satisfies multiple conditions | `{ reviews: { $elemMatch: { rating: 5, user: "Alice" } } }` → matches docs where a single `reviews` element has both `rating: 5` and `user: "Alice"` |
| Dot notation | Query a specific array element by index                                 | `{ "tags.0": "red" }` → matches docs where the first element in `tags` is `"red"`                                                                    |




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
