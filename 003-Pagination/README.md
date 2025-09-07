# Sorting, Limiting, Skipping & Pagination

## 1. Sort

- `.sort()` orders the document returned by a query
- **Syntax:**
    ```javascript
    db.collection.find(<query>).sort({ <field1>: <order>, <field2>: <order>, ... })
    ```
- **Examples:**
    ```javascript
    // Sort users by age ascending
    db.users.find().sort({ age: 1 })

    // Sort by age descending
    db.users.find().sort({ age: -1 })

    // Sort by multiple fields: age ascending, name descending
    db.users.find().sort({ age: 1, name: -1 })
    ```

## 2. Limit
- `.limit()` restricts the number of documents returned
- **Syntax:**
    ```javascript
    db.collection.find(<query>).limit(<number>)
    ```
- **Example:**
    ```javascript
    // Get only the first 5 documents
    db.users.find().limit(5)
    ```

## 3. Skip
- `.skip()` skips a number of documents in the query result
- **Syntax:**
    ```javascript
    db.collection.find(<query>).skip(<number>)

    ```
- **Example:**
    ```javascript
    // Skip first 5 documents
    db.users.find().skip(5)
    ```

## Chaining

- **Example**:
    ```javascript
    // Top 3 youngest users
    db.users.find().sort({ age: 1 }).limit(3)
    ```

- **Example:**
    ```javascript
    // skip first 5, next 5, sorted by age ascending
    db.users.find().sort({ age: 1 }).skip(5).limit(5)
    ```
## Pagination
- Pagination is simply the technique of splitting a large set of results into smaller, manageable chunks or pages.
- In MongoDB pagination is implemented using a combination of:
    - `limit()` - how many documents to show per page
    - `skip()` - how many documents to skip before starting to return results
    - `sort()` - optional, to maintain consistent ordering
- **Example:** Assume we have a users collection and want 5 users per page, sorted by age descending:

```javascript

// To know total number of pages
const totalUsers = db.users.countDocuments();
const pageSize = 5;
const totalPages = Math.ceil(totalUsers / pageSize);

// Page 1: first 5 users
db.users.find().sort({ age: -1 }).skip(0).limit(5)

// Page 2: next 5 users
db.users.find().sort({ age: -1 }).skip(5).limit(5)

// Page 3: next 5 users
db.users.find().sort({ age: -1 }).skip(10).limit(5)
```

> [!IMPORTANT]  
> Always use .sort() when paginating, otherwise documents may appear in arbitrary order across pages.