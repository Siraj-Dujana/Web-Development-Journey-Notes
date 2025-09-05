# Fist install mongodb(https://www.mongodb.com/try/download/community)
# and mongosh(https://www.mongodb.com/try/download/shell).


## *Shell:* is a program that allows users to execute commands.
## *Terminal:* lets you interact with the shell.



# steps to follow.

1. **Connect to MongoDB:**
   - Open a new PowerShell or Command Prompt window.
   - Run:
     ```powershell
     mongosh
     ```
     This will connect you to the MongoDB shell.
     if mongosh is not installed then first install it then add path in Environment Variables.

2. **Verify the Databases:**
   - Once in the shell, type:
     ```javascript
     show dbs
     ```
     to see the list of databases.

3. **Review Service Status:**
   - You can always check the status of your MongoDB service by running:
     ```powershell
     net start MongoDB
     ```


# **Intro to MongoDB**  

MongoDB is a **NoSQL, document-based database** that stores data in **JSON-like BSON documents** instead of tables. It is **flexible, scalable, and high-performance**, making it ideal for modern applications.  

### **🔹 Key Features**  
✅ **Schema-less** (Flexible structure)  
✅ **High performance** (Fast reads/writes)  
✅ **Horizontally scalable** (Sharding)  
✅ **Rich queries** (Filtering, indexing, aggregation)  

### **🔹 Basic Commands**  
```shell
mongosh                 #to start
show dbs                 # List databases  
use myDB                 # Switch/create DB  
show collections         # List collections 
db                      #print current database name 
cls                     # to clear screen
db.users.insertOne({ name: "Alice", age: 25 })  # Insert  
db.users.find()          # Retrieve data  
```

### **🔹 Why Use MongoDB?**  
⚡ Ideal for **real-time apps, e-commerce, IoT, and big data** applications.  

MongoDB is **fast, flexible, and powerful**—perfect for modern development! 🚀



## Mongoshell also recognize most of the methods and properties of javascript.


### **Temporary vs Permanent Databases in MongoDB**  

- **Temporary**: A database **disappears** after restart if no data is inserted.  
- **Permanent**: A database **persists** once a document is added.  

**Example:**  
```shell
use tempDB       # Temporary (not saved yet)
db.users.insertOne({ name: "Alice" })  # Becomes permanent
```  
🔹 **Databases exist permanently only if they contain data!** 🚀


**JSON vs BSON in MongoDB:**  

- **JSON (JavaScript Object Notation)**: A lightweight, human-readable format for data exchange. Used for client-server communication but not directly for MongoDB storage.  

- **BSON (Binary JSON)**: A binary format used internally by MongoDB for efficient data storage and retrieval. Supports additional data types like `Date`, `Decimal128`, and `ObjectId`, which JSON doesn't.  

### Key Differences:  
| Feature      | JSON | BSON |
|-------------|------|------|
| **Format**  | Text-based | Binary |
| **Readability** | Human-readable | Not human-readable |
| **Size**    | Larger | More compact (but with some overhead) |
| **Performance** | Slower parsing | Faster parsing |
| **Data Types** | Limited | Supports more types (e.g., `Date`, `BinData`) |

MongoDB stores data in **BSON** for efficiency but allows interaction using **JSON-like** queries. 🚀

### **Document vs Collection in MongoDB**  

- **Document**: A single record (BSON format), like a row in SQL.  
- **Collection**: A group of documents, like a table in SQL.  

📌 **Example:** A `users` collection contains multiple user documents. 🚀


# Insert

- **Inserting Data:** If a collection doesn’t exist, it is automatically created when you first insert a document.  

### **Example Commands:**  
```javascript
// Insert a single document (correct syntax)
db.student.insertOne({ name: "Siraj", marks: 97 });

// Show all collections in the database
show collections;

// Retrieve all documents in the student collection
db.student.find();
```

💡 **Note:** Your insert syntax had a small issue—field names and values should be inside `{}`. 🚀

### **Insert Multiple Documents in MongoDB**  

Use `insertMany()` to insert multiple documents at once.  

### **Example:**  
```javascript
db.student.insertMany([
  { name: "Siraj", marks: 97 },
  { name: "Aisha", marks: 89 },
  { name: "Rahul", marks: 92 }
]);
```

💡 **Key Points:**  
- Inserts multiple documents into the `student` collection.  
- If the collection doesn’t exist, MongoDB creates it automatically.  
- Returns an acknowledgment with inserted IDs. 🚀

### **MongoDB Queries & Cursor**  

#### **1️⃣ Find Multiple Documents (`find()`)**  
Retrieves all matching documents. Returns a **cursor** (an iterable result set).  
```javascript
db.student.find({ marks: 97 });
```
🔹 Returns all documents where `marks` is `97`.  

#### **2️⃣ Find a Single Document (`findOne()`)**  
Returns only the first matching document.  
```javascript
db.student.findOne({ name: "Siraj" });
```
🔹 Returns the first document where `name` is `"Siraj"`.  

#### **3️⃣ Cursor in MongoDB**  
A **cursor** is an iterable object returned by `find()`, allowing you to navigate through results.  
Example:  
```javascript
var cursor = db.student.find();
while (cursor.hasNext()) {
   printjson(cursor.next());
}
```
💡 `findOne()` returns a document directly, while `find()` returns a cursor (a set of documents). 🚀

### **Commonly Used MongoDB Operators**  

#### **1️⃣ Query Operators (Used in `find()`)**  
| Operator | Description | Example |
|----------|-------------|------------|
| `$eq` | Equals | `{ marks: { $eq: 90 } }` |
| `$ne` | Not equal | `{ marks: { $ne: 50 } }` |
| `$gt` | Greater than | `{ marks: { $gt: 80 } }` |
| `$lt` | Less than | `{ marks: { $lt: 60 } }` |
| `$in` | Matches any in array | `{ name: { $in: ["Siraj", "Aisha"] } }` |
| `$or` | Matches any condition | `{ $or: [{ marks: { $gt: 90 } }, { name: "Aisha" }] }` |

#### **2️⃣ Update Operators (Used in `updateOne()` / `updateMany()`)**  
| Operator | Description | Example |
|----------|-------------|------------|
| `$set` | Updates a field | `{ $set: { marks: 95 } }` |
| `$inc` | Increments a value | `{ $inc: { marks: 5 } }` |
| `$push` | Adds to an array | `{ $push: { subjects: "English" } }` |
| `$pull` | Removes from an array | `{ $pull: { subjects: "Math" } }` |

#### **3️⃣ Projection Operator (Used in `find()`)**  
| Operator | Description | Example |
|----------|-------------|------------|
| `$exists` | Checks if field exists | `{ age: { $exists: true } }` |
| `$type` | Matches field type | `{ age: { $type: "int" } }` |

💡 **Example Usage:**  
```javascript
db.student.find({ marks: { $gt: 80 } }); // Find students with marks > 80
db.student.updateOne({ name: "Siraj" }, { $set: { marks: 98 } }); // Update marks
```
🚀 These are the most commonly used MongoDB operators!

### **MongoDB Update Operations**  

#### **1️⃣ `updateOne()`** – Updates the first matching document  
```javascript
db.student.updateOne({ name: "Siraj" }, { $set: { marks: 95 } });
```
🔹 Updates `marks` to `95` for the first document where `name` is "Siraj".  

#### **2️⃣ `updateMany()`** – Updates all matching documents  
```javascript
db.student.updateMany({ marks: { $lt: 50 } }, { $set: { status: "Failed" } });
```
🔹 Adds `status: "Failed"` to all students with marks less than `50`.  

#### **3️⃣ `replaceOne()`** – Replaces an entire document  
```javascript
db.student.replaceOne(
  { name: "Aisha" }, 
  { name: "Aisha", marks: 88, status: "Passed" }
);
```
🔹 Replaces the entire document for `"Aisha"` (removes other fields if they exist).  

#### **4️⃣ Common Update Operators**  
| Operator | Description | Example |
|----------|-------------|------------|
| `$set` | Updates a field | `{ $set: { marks: 95 } }` |
| `$inc` | Increments a value | `{ $inc: { marks: 5 } }` |
| `$mul` | Multiplies a value | `{ $mul: { marks: 1.1 } }` |
| `$rename` | Renames a field | `{ $rename: { "marks": "score" } }` |
| `$unset` | Removes a field | `{ $unset: { status: "" } }` |

🚀 **Example:**  
```javascript
db.student.updateOne({ name: "Rahul" }, { $inc: { marks: 5 } });
```
🔹 Increases `marks` by `5` for `"Rahul"`.

### **Nesting in MongoDB**  

MongoDB allows **nested documents (subdocuments)** within a document, enabling structured and flexible data storage.  

#### **Example: Nested Document Structure**  
```json
{
  "_id": ObjectId("67bca73484c6cc52c0fa4214"),
  "name": "Saifullah",
  "performance": { 
    "marks": 100, 
    "grade": "A" 
  }
}
```
### **Querying Nested Fields**  

#### **1️⃣ Find a Document Based on a Nested Field**
```javascript
db.student.find({ "performance.marks": 100 });
```
🔹 Finds students with `marks = 100`.  

#### **2️⃣ Update a Nested Field (`$set`)**
```javascript
db.student.updateOne(
  { name: "Saifullah" },
  { $set: { "performance.grade": "A+" } }
);
```
🔹 Updates `grade` inside `performance`.  

#### **3️⃣ Increment a Nested Field (`$inc`)**
```javascript
db.student.updateOne(
  { name: "Saifullah" },
  { $inc: { "performance.marks": 5 } }
);
```
🔹 Increases `marks` by `5`.  

#### **4️⃣ Remove a Nested Field (`$unset`)**
```javascript
db.student.updateOne(
  { name: "Saifullah" },
  { $unset: { "performance.grade": "" } }
);
```
🔹 Removes `grade` from `performance`.  

💡 **Nesting helps store related data efficiently without needing multiple collections!** 🚀


# Connecting Mongoose Packaged to connect mongo db with Node.js and Express.js





