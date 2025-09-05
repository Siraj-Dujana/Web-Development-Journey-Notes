using node.js and MYSQL

Faker: To generate fake data.
userid > username > email > password
npm i @faker-js/faker

inistall 
let getuser=()=>{
return [
    faker.datatype.uuid(),
    faker.internet.userName(),
    faker.internet.email(),
    faker.internet.password(),
];
};

Yes! The difference is in the **module system**:  

- **ESM (ECMAScript Modules)** → `import { faker } from '@faker-js/faker';`  
  - Uses `import/export` syntax  
  - Requires `"type": "module"` in `package.json`  
  - Preferred for modern JavaScript  

- **CJS (CommonJS)** → `const { faker } = require('@faker-js/faker');`  
  - Uses `require()` syntax  
  - Default in Node.js  
  - Works without `"type": "module"`  

Use **ESM** for modern projects and **CJS** for compatibility with older code. 🚀Yes! The difference is in the **module system**:  

- **ESM (ECMAScript Modules)** → `import { faker } from '@faker-js/faker';`  
  - Uses `import/export` syntax  
  - Requires `"type": "module"` in `package.json`  
  - Preferred for modern JavaScript  

- **CJS (CommonJS)** → `const { faker } = require('@faker-js/faker');`  
  - Uses `require()` syntax  
  - Default in Node.js  
  - Works without `"type": "module"`  

Use **ESM** for modern projects and **CJS** for compatibility with older code. 🚀

MySQL2 Package
To connect Node with Mysql

connection.end();// to close connection

client > server > database
client < server < database

install mysql 2

// Get the client
const mysql = require('mysql2');

// Create the connection to database
const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  database: 'test',
});

// A simple SELECT query
connection.query(
  'SELECT * FROM `table` WHERE `name` = "Page" AND `age` > 45',
  function (err, results, fields) {
    console.log(results); // results contains rows returned by server
    console.log(fields); // fields contains extra meta data about results, if available
  }
);


#### using SQL from CLI
/usr/local/mysql/bin/mysql -u root -p


1. Search for `mysql.exe` in File Explorer to find MySQL's installation path.

2. In PowerShell or Command Prompt, navigate to the folder where `mysql.exe` is located. For example:

   ```powershell
        & "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p
   ```


different methods to interact with Databases
1. workbench
2. node js 
3. cli
4. run sql big queries (if workbench is not installed)
    create file schema.sql
    source schema.sql //in cli



creating table
create TABLE user(
id varchar(50) primary key,
username varchar(50) unique,
email varchar(50) unicode not null,
password varchar(50) not null
);


Placeholders (`?`) in SQL queries are used to safely insert values. Instead of directly embedding values in the query, placeholders allow the values to be passed separately, preventing SQL injection.

Example:
```sql
SELECT * FROM users WHERE name = ? AND age = ?
```

In the code, the `?` is replaced with actual values when the query runs. This makes the query safer and more flexible.


//insert just one user
// let query="INSERT INTO user VALUES(?,?,?,?)";
// let user=["1","siraj","abc@gmail.com","123"];

//inserting multiple users
let query="INSERT INTO user VALUES ?";
let users=[
  ["2","siraja","abc@gmail.coma","1235"],
  ["3","sirajb","abc@gmail.comb","1234"],
];

try {
    connection.query(query,[users],(err, results)=> {
        if(err) throw err;
        console.log(results); // results contains rows returned by server
      }
    );
} catch (error) {
    console.log(error)
}



inserting bulk data usinf faker

let getRandomUser = () => {
  return [
     faker.string.uuid(),
     faker.internet.username(), // before version 9.1.0, use 
     faker.internet.email(),
     faker.internet.password()
  ];
};
let data=[];
for(let i=1;i<=100;i++){
  data.push(getRandomUser())//100 users data
  

}

console.log(data)
let query="INSERT INTO user (id,name,email,password) VALUES ?";
try {
    connection.query(query,[data],(err, results)=> {
        if(err) throw err;
        console.log(results); // results contains rows returned by server
      }
    );
} catch (error) {
    console.log(error)
}

connection.end();

NOTE: The relationship between them is that data fills in the dynamic parts (placeholders) of the query.

ROUTING
REST
get / > show no of users in database 

get /user > show users(email,id,username) ejs.

PATCH /user/:id > username edit

POST /user > new user

delete /user/:id > user delete


