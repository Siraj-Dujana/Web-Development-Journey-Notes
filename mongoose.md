### **Mongoose Definitions with Your Code**  

1️⃣ **Mongoose** – A **Node.js library** used to interact with MongoDB by providing schema-based data modeling.  
```javascript
const mongoose = require('mongoose');
```

2️⃣ **Schema** – Defines the structure of documents in a MongoDB collection.  
```javascript
const userschema = new mongoose.Schema({
    name: String,
    age: Number,
    email: String
});
```

3️⃣ **Model** – A **wrapper** around a schema that allows querying and data manipulation.  
```javascript
const User = mongoose.model("User", userschema);
```

4️⃣ **insertOne** – Inserts a **single document** into MongoDB.  
```javascript
const user2 = new User({
    name: "Dujana",
    age: 20,
    email: "sirajdujana16@gmail.com"
});

user2.save()
.then(() => console.log("Inserted Successfully ✅"))
.catch(err => console.log(err));
```

5️⃣ **insertMany** – Inserts **multiple documents** at once.  
```javascript
User.insertMany([
    { name: "aaqib", age: 29, email: "aaqib@gmail.com" },
    { name: "mubeen", age: 20, email: "mubeen@gmail.com" },
    { name: "Ahmed", age: 5, email: "ahmed@gmail.com" }
])
.then(res => console.log(res))
.catch(err => console.log(err));
```

6️⃣ **Buffer Operations** – Mongoose buffers commands internally when the database connection isn't ready yet, so queries **can still execute after reconnection**.  

```javascript
main().then(() => {
    console.log("Connection successful ✅");
}).catch(err => console.log(err));

async function main() {
    await mongoose.connect('mongodb://127.0.0.1:27017/test');
}
```

This ensures MongoDB commands **don't fail** if executed before the connection is established.

### **Mongoose Query Methods**

Mongoose queries return a **Query Object**, which is not a promise but has a `.then()` method for promise-like behavior. Here’s a quick overview of common query methods:

---

#### **1. `Model.find()`**
Finds all documents matching the filter.

```javascript
User.find({ age: { $gte: 47 } }) // Find users with age >= 47
    .then((data) => console.log(data))
    .catch((err) => console.error(err));
```

---

#### **2. `Model.findOne()`**
Finds the first document matching the filter.

```javascript
User.findOne({ age: { $gte: 47 } }) // Find first user with age >= 47
    .then((data) => console.log(data))
    .catch((err) => console.error(err));
```

---

#### **3. `Model.updateOne()`**
Updates the first document matching the filter.

```javascript
User.updateOne({ name: "siraj" }, { name: "mubeen" }) // Update name
    .then((data) => console.log(data))
    .catch((err) => console.error(err));
```

---

#### **4. `Model.updateMany()`**
Updates all documents matching the filter.

```javascript
User.updateMany({ age: { $gte: 47 } }, { isActive: true }) // Update all users with age >= 47
    .then((data) => console.log(data))
    .catch((err) => console.error(err));
```

---

#### **5. `Model.findOneAndUpdate()`**
Finds and updates a document. By default, it returns the **original document**. Use `{ new: true }` to return the updated document.

```javascript
User.findOneAndUpdate(
    { name: "siraj" }, 
    { name: "mubeen" }, 
    { new: true } // Return the updated document
).then((res) => console.log(res))
 .catch((err) => console.error(err));
```

---

#### **6. `Model.deleteOne()`**
Deletes the first document matching the filter.

```javascript
User.deleteOne({ name: "siraj" }) // Delete user with name "siraj"
    .then((res) => console.log(res))
    .catch((err) => console.error(err));
```

---

#### **7. `Model.deleteMany()`**
Deletes all documents matching the filter.

```javascript
User.deleteMany({ name: "aaqib" }) // Delete all users with name "aaqib"
    .then((res) => console.log(res))
    .catch((err) => console.error(err));
```

---

#### **8. `Model.findOneAndDelete()`**
Finds and deletes a document. Returns the deleted document.

```javascript
User.findOneAndDelete({ name: "siraj" }) // Find and delete user
    .then((res) => console.log(res))
    .catch((err) => console.error(err));
```

---

### **Key Notes**
- Mongoose queries are **not promises** but have a `.then()` method.
- Use `{ new: true }` in `findOneAndUpdate` to return the **updated document**.
- Use `.catch()` to handle errors.

---


### **Basic Schema Types**
Mongoose supports various schema types for defining fields:

```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
    name: String,               // String type
    age: Number,                // Number type
    isActive: Boolean,         // Boolean type
    createdAt: Date,           // Date type
    hobbies: [String],          // Array of strings
    address: {                 // Nested object
        city: String,
        country: String
    },
    email: {                   // With additional options
        type: String,
        required: true,
        unique: true
    },
    salary: {                  // Number with min/max
        type: Number,
        min: 0,
        max: 100000
    },
    role: {                    // Enum (specific values)
        type: String,
        enum: ['admin', 'user', 'guest'],
        default: 'user'
    },
    bio: {                     // Custom validation
        type: String,
        validate: {
            validator: (v) => v.length <= 100,
            message: 'Bio must be 100 characters or less.'
        }
    }
});

const User = mongoose.model('User', userSchema);
```

---

### **Common SchemaType Options**
Each field can have additional options:

| Option        | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `type`        | Data type (e.g., `String`, `Number`, `Date`, `Boolean`, etc.).              |
| `required`    | If `true`, the field is mandatory.                                          |
| `default`     | Default value if no value is provided.                                      |
| `min` / `max` | Minimum and maximum values for `Number` types.                              |
| `minlength` / `maxlength` | Minimum and maximum lengths for `String` types.                     |
| `enum`        | Restricts the value to a specific set of strings.                           |
| `unique`      | Ensures the field value is unique across documents.                         |
| `validate`    | Custom validation function.                                                 |

---

### **Example Usage**

#### 1. **Creating a Document**
```javascript
const newUser = new User({
    name: "John Doe",
    age: 30,
    isActive: true,
    email: "john@example.com",
    salary: 50000,
    role: "admin",
    bio: "I love coding!"
});

newUser.save()
    .then((doc) => console.log(doc))
    .catch((err) => console.error(err.message));
```

#### 2. **Validation Errors**
If validation fails (e.g., `age` is negative):
```javascript
const invalidUser = new User({ age: -10 });
invalidUser.save()
    .catch((err) => console.error(err.message)); // Output: Validation error
```

#### 3. **Updating with Validation**
Enable validation during updates:
```javascript
User.updateOne(
    { name: "John Doe" },
    { age: -10 }, // Invalid age
    { runValidators: true }
).catch((err) => console.error(err.message)); // Output: Validation error
```

---

### **Custom Schema Types**
You can also create custom types using Mongoose's `Schema.Types`:

```javascript
const profileSchema = new mongoose.Schema({
    userId: mongoose.Schema.Types.ObjectId, // MongoDB ObjectId
    metadata: mongoose.Schema.Types.Mixed,  // Flexible mixed type
    settings: mongoose.Schema.Types.Map     // Key-value pairs
});
```

---

### **Summary**
- Use schema types (`String`, `Number`, `Date`, etc.) to define fields.
- Add options like `required`, `default`, `min`, `max`, `enum`, etc.
- Use `validate` for custom validation logic.
- Enable `runValidators` for validation during updates.

This ensures your data is structured and validated properly!