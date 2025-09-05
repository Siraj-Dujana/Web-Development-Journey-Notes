🚀 Node.js - JavaScript Runtime Environment

Node.js is a JavaScript runtime that allows you to run JavaScript code outside the browser. It is commonly used for server-side programming, building APIs, and real-time applications like chat or gaming servers.

⚠️ Node.js is NOT a language, library, or framework!


 📌 Features of Node.js
✅ Popular - Widely used in the industry.  
✅ JavaScript-Based - No need to learn another language.  
✅ Asynchronous & Event-Driven - Efficient and scalable.  
✅ Non-blocking I/O - Handles multiple requests simultaneously.  
✅ Cross-platform - Works on Windows, macOS, and Linux.  



 🛠 Steps to Run Node.js
1️⃣ Install Node.js from [nodejs.org](https://nodejs.org/)  
2️⃣ Save code in a file (e.g., server.js).  
3️⃣ Run the file in terminal:  
   sh
   node server.js
   
4️⃣ Access the server at http://localhost:3000 (if applicable).  



 🖥 Node REPL (Read-Evaluate-Print Loop)
💡 Interactive environment to run JavaScript code in the terminal.  
✅ Commands:  
   .help → Lists available REPL commands.  
   .exit → Exits REPL mode.  

⚠️ DOM manipulation is NOT possible in Node REPL!



 🌍 Global Object in Node.js
Similar to window in the browser, Node.js provides a global object.  

Example:
js
console.log(global);




 🔄 Running Node.js Files
To execute a JavaScript file in Node.js:
sh
node filename.js

Example:
js
console.log('Hello from Node.js!');

Run using:
sh
node hello.js




 ⚙️ Process Object
Provides information and control over the current Node.js process.
It is a global object in Node.js that gives details about the currently running Node.js process (the instance of Node running your code).
📌 Common Methods:
- process.argv → Returns an array of command-line arguments.
- process.release → Shows Node.js version.
- process.cwd() → Returns the current working directory.

Example:
js
let args = process.argv;
for (let i = 2; i < args.length; i++) {
    console.log(args[i]);
}

Run using:
sh
node script.js arg1 arg2




 📦 Module System in Node.js
🔹 module.exports → Exports functions and properties to another file.  
🔹 require() → Imports external modules.

# Example 1: Exporting a Value
📄 math.js
js
module.exports = 123;

📄 export.js
js
const someValue = require('./math');
console.log(someValue); // Output: 123


# Example 2: Exporting a Function
📄 math.js
js
module.exports.add = (a, b) => a + b;

📄 app.js
js
const math = require('./math');
console.log(math.add(5, 3)); // Output: 8




 📁 NPM (Node Package Manager)
NPM is the package manager for Node.js, allowing developers to install and manage dependencies.

# ✅ Why use NPM?
- 📌 Library of Packages - Reusable code.
- 📌 Command-line tool - Install, update, and manage packages.

# 🛠 Installing Packages
sh
npm install <package-name>

Example:
sh
npm install figlet




 📂 node_modules & package.json
🔹 node_modules → Contains all installed dependencies of a project.  
🔹 package.json → Stores project metadata and dependencies.  

# 🛠 Creating package.json
sh
npm init


# 🛠 Installing Dependencies from package.json
sh
npm install




 🎨 Using figlet (Example Package)
📄 index.js
js
const figlet = require('figlet');

figlet('Hello World!', function (err, data) {
    if (err) {
        console.log('Something went wrong...');
        console.dir(err);
        return;
    }
    console.log(data);
});

Run using:
sh
node index.js




 🌍 Global vs Local Package Installation
📌 Local Installation (Project-Specific)
sh
npm install package-name

📌 Global Installation (System-Wide)

sh
npm install -g package-name

📌 Uninstall a Global Package
sh
npm uninstall -g package-name




 🔄 Linking Global Packages
sh
npm link <package-name>

📌 If permission issues occur:
sh
npm config set prefix "C:\Users\<YourUsername>\npm-global"




 📜 require vs import
| Feature                 | require() | import |

| Selective Loading       | ❌ No     | ✅ Yes |
| Execution               | Synchronous| Asynchronous |
| Module Type             | CommonJS  | ES6 |

# Example:
📄 math.js
js
export function sum(a, b) {
    return a + b;
}

📄 app.js
js
import { sum } from "./math.js";
console.log(sum(5, 3)); // Output: 8




 📌 Missing Topics (Consider Adding)
✅ Event Loop - Understanding how Node.js handles asynchronous tasks.  
✅ Streams & Buffers - For handling large amounts of data efficiently.  
✅ File System Module - Reading & writing files in Node.js.  
✅ Express.js - A popular web framework for Node.js.  
✅ Debugging Node.js Applications  



🔥 Now you have a structured and well-organized Node.js guide! 🚀

