## 🔹 Step 1: Check If MongoDB  Is Installed

1. Open **File Explorer** and go to:
   ```
   C:\Program Files\MongoDB\Server\7.0\bin
   ```
2. If **YES**, MongoDB is installed but not added to **PATH**. Move to **Step 2**.
3. If **NO**, MongoDB is not installed. Move to **Step 3**.

---

## 🔹 Step 2: Add MongoDB to System PATH (Fix `mongod` Not Found)

1. Open **Windows Search** and type **"Environment Variables"**, then click **"Edit the system environment variables"**.
2. Click **"Environment Variables"**.
3. Under **System Variables**, find and select `Path`, then click **Edit**.
4. Click **New**, then **paste this path** (update it based on your version):
   ```
   C:\Program Files\MongoDB\Server\7.0\bin
   ```
5. Click **OK** → **OK** → **Restart Your Computer**.

---

## 🔹 Step 3: Verify MongoDB Installation

After restarting, open **PowerShell** or **Command Prompt** and run:

```powershell
mongod --version
```

- If it **shows a version number**, MongoDB is set up correctly! 🎉
- If it **still says "not recognized"**, MongoDB is not installed.



#
#
#
# once the path problem is fixed then go a head for another problem (if access is denied).
---
#
#
#


The **"System error 5: Access is denied"** error means that you don’t have the necessary administrative privileges to start MongoDB as a service. Here’s how to fix it:

---

## **🔹 Solution 1: Run Command Prompt as Administrator**
1. **Click on Windows Start** → Type **cmd** (Command Prompt).
2. **Right-click on "Command Prompt"** → Click **"Run as Administrator"**.
3. Now, try running the command again:
   ```powershell
   net start MongoDB
   ```
   If it works, MongoDB is now running!

---

# if step 1 not work then go for step 2

## **🔹 Solution 2: Check User Permissions**
If the issue persists, MongoDB **might not have the right permissions** to run as a service:

1. **Open Windows Run (`Win + R`)** → Type **services.msc** → Press **Enter**.
2. Find **MongoDB** in the list.
3. **Right-click on MongoDB** → Click **Properties**.
4. Go to the **Log On** tab.
5. Select **Local System account** → Click **OK**.
6. Try starting MongoDB again:
   ```powershell
   net start MongoDB
   ```

---

# Great news! 🎉 The service started successfully, so MongoDB is now up and running.

### Steps (path for mongosh C:\Users\Super Galaxy\AppData\Local\Programs\mongosh\)
 
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

