# MongoDB

MongoDB is a NoSQL database that stores data in a flexible, JSON-like format instead of traditional rows and columns.

## Key features

- **Document-Oriented:** Stores data as BSON documents (similar to JSON)
- **Schema-less:** Collections don’t require a fixed structure; documents in the same collection can have different fields
- **Scalable:** Built for horizontal scaling (sharding)
- **High Performance:** Optimized for read/write speed
- **Rich Query Language:** Supports filters, aggregations, indexes, and full-text search

## How data is organised

- **Database:** Holds collections
- **Collections:** Similar to a table (but schema-less)
- **Document:** Similar to a row/ record (but stores as JSON like objects in BSON format)
- **Field:** Similar to a column (a key-value pair inside a document)

## Important Commands

- `sudo systemctl start mongod` - Start MongoDB server
- `sudo systemctl status mongod` - Check MongoDB server status
- `sudo systemctl stop mongod` - Stop MongoDB server
- `sudo systemctl enable mongod` - Ensures to auto-start on boot
- `mongosh` - Start MongoDB shell
- `mongodb-compass` - Launch MongoDB Compass (GUI)

## Important points
- **Default port:** `27017` (When `mongod` is started, it listens on this port unless configured otherwise)
- **Config File (Ubuntu):** `/etc/mongod.conf`
- **Log File (Ubuntu):** `/var/log/mongodb/mongod.log`

## Important queries
- `show dbs` - Show all databases
- `use database_name` - Use a particular database
- `show collections` - List collections in current database
- `db.dropDatabase()` - Drop the current database
- `db.collection.drop()` - drop a collection

## CRUD Operations

- **C** - Create
- **R** - Read
- **U** - Update
- **D** - Delete