### Unit 1 Topic
1. **Introdunction**  
2. **Why Use DBMS?**  
3. **Where is a Database Management System (DBMS) Being Used?**  
4. **Components of DBMS**  
5. **Database Languages**  
   - Data Definition Language  
   - Data Manipulation Language  
   - Data Control Language  
   - Transactional Control Language  
   - Data Query Language (DQL)  
6. **Database Management System**  
7. **Applications of DBMS**  
8. **Paradigm Shift from File System to DBMS**  
9. **Advantages of DBMS**
10. **Transaction Management in DBMS**  
   - Definition and Purpose  
   - ACID Properties:  
     - Atomicity  
     - Consistency  
     - Isolation  
     - Durability  
   - Key Components of Transaction Management:  
     - Transaction Coordinator  
     - Concurrency Control  
     - Recovery System  

11. **Structure of a DBMS**  
   - Components:  
     - Hardware  
     - Software:  
       - DBMS Engine  
       - Query Processor  
       - Storage Manager  
       - Transaction Manager  
       - Concurrency Control Manager  
       - Recovery Manager  
     - Data:  
       - Database Schema  
       - Tables  
       - Indexes  
       - Views  
     - Users:  
       - Database Administrators (DBAs)  
       - Developers  
       - End Users  

12. **Architectural Layers of a DBMS**  
   - External Level (User View Layer)  
   - Conceptual Level (Logical View Layer)  
   - Internal Level (Physical View Layer)  

13. **Interaction of Components**  
   - Query Execution  
   - Transaction Management  
   - Concurrency Control  
   - Recovery  

14. **Definition of Transaction in DBMS**
15. **Operations of Transaction**:
   - Read(X)
   - Write(X)
   - Commit
   - Rollback
16. **Transaction Schedules**:
   - Serial Schedule
   - Non-Serial Schedule
17. **Serializable Transactions**
18. **States of a Transaction**:
   - Active
   - Partially Committed
   - Committed
   - Failed
   - Aborted
---

### **Topic 1:What is DBMS?**  
**DBMS (Database Management System)** is software that helps us store, organize, retrieve, and manage data in a structured way. Instead of manually handling large amounts of data, DBMS makes it easy to manage it efficiently. Examples include MySQL, Oracle, and Microsoft Access.

### **Topic 2:Why Do We Use DBMS?**  
1. **Organized Data Storage**: It stores data systematically so we can easily find and use it.  
2. **Efficient Data Handling**: Makes it faster and easier to add, update, or retrieve data.  
3. **Data Security**: Controls who can access or edit data to prevent unauthorized use.  
4. **Data Integrity**: Ensures data is accurate and consistent across the system.  
5. **Concurrent Access**: Allows multiple people to access the same data without conflicts.  
6. **Backup and Recovery**: Protects data by saving copies and recovering it in case of system failures.  
7. **Time Saving**: Speeds up the development of applications by handling complex data management tasks.  

### **Topic 3: Where is DBMS Being Used?**  
DBMS is widely used across various industries to store and manage large volumes of data efficiently. Here are some key applications:

1. **Airlines**:  
   - DBMS is used to manage flight reservations, schedules, and customer information.  
   - For example, it helps airlines handle millions of booking and flight records efficiently.

2. **Telecom**:  
   - Manages customer details, call records, and network usage.  
   - Keeps track of prepaid and postpaid bills and user activities.

3. **Universities**:  
   - Stores student information, including registration details, grades, and course enrollments.  
   - Simplifies administration by organizing large data sets for staff and students.

4. **Sales**:  
   - Helps track product information, purchases, and customer details.  
   - Used in retail systems to ensure smooth inventory management and customer service.

5. **Banking**:  
   - Manages customer accounts, transactions, loans, and credit card records.  
   - Ensures secure and accurate handling of financial data.


### **Topic 4: Database Languages**  
Database languages are used to interact with a DBMS. These languages let users define, manipulate, control, and query the data in the database. Here’s a simple breakdown of the main types:

---

#### **1. Data Definition Language (DDL)**  
- DDL is used to **define the structure** of the database (like tables, indexes, etc.).  
- Think of it as setting up the "skeleton" of the database.  
- Common DDL Commands:
  - **CREATE**: Creates a database object (like tables or views).  
    *Example*: Create a table to store student data.  
  - **ALTER**: Modifies the structure of an existing database object.  
    *Example*: Add a new column for student phone numbers.  
  - **DROP**: Deletes an object from the database.  
    *Example*: Remove a table that's no longer needed.  
  - **TRUNCATE**: Deletes all records in a table but keeps the structure.  
  - **RENAME**: Renames database objects.  
  - **COMMENT**: Adds comments to the data dictionary for better understanding.

---

#### **2. Data Manipulation Language (DML)**  
- DML is used to **manipulate the data** within the database.  
- Think of it as editing or fetching data from tables.  
- Common DML Commands:
  - **SELECT**: Fetches data from a database without modifying it.  
    *Example*: View all students enrolled in a course.  
  - **INSERT**: Adds new records to a table.  
    *Example*: Add a new student to the database.  
  - **UPDATE**: Changes existing data in a table.  
    *Example*: Update a student's address.  
  - **DELETE**: Removes records from a table.  
    *Example*: Remove a student who has graduated.  
  - **MERGE**: Combines INSERT and UPDATE operations (UPSERT).

---

#### **3. Data Control Language (DCL)**  
- DCL is used to **control access to the database**.  
- Think of it as managing permissions for users.  
- Common DCL Commands:
  - **GRANT**: Gives a user permission to perform specific tasks (like SELECT or INSERT).  
    *Example*: Allow a teacher to view student data.  
  - **REVOKE**: Removes permissions from a user.  
    *Example*: Deny access to modify financial records.

---

#### **4. Transaction Control Language (TCL)**  
- TCL manages **transactions** in the database.  
- Think of a transaction as a group of operations that must be treated as a single unit (like transferring money).  
- Common TCL Commands:
  - **COMMIT**: Saves changes permanently.  
    *Example*: Finalize a money transfer.  
  - **ROLLBACK**: Reverts changes made during a transaction.  
    *Example*: Cancel a failed transaction.  
  - **SAVEPOINT**: Creates a temporary checkpoint in a transaction.  
    *Example*: Save progress before a complex update.

---

#### **5. Data Query Language (DQL)**  
- DQL is a subset of DML focused solely on **fetching data**.  
- The main command in DQL is:
  - **SELECT**: Retrieves data from the database.  
    *Example*: Find all students who scored above 90%.

---

#### Why Are These Languages Important?  
1. **DDL** creates and organizes the database structure.  
2. **DML** allows users to work with the actual data.  
3. **DCL** ensures that data access is secure.  
4. **TCL** ensures transactions are reliable and consistent.  
5. **DQL** helps retrieve essential information for decision-making.  

In simple terms, these languages are tools that help us *build*, *edit*, *control*, and *use* databases effectively.

---

### **Topic 5: Database Management System (DBMS)**  

A **Database Management System (DBMS)** is software that helps us manage data efficiently and securely. It provides tools and functions to store, organize, and retrieve data in a structured way.

---

### **Topic 6: What Does DBMS Do?**  
A DBMS acts like a smart assistant for handling databases. Here’s what it helps with:  
1. **Data Definition**:  
   - DBMS lets us define the structure of the database (tables, relationships, etc.).  
   - Example: Creating a table for storing student details.  

2. **Data Storage**:  
   - Stores data in an organized and systematic way, making it easy to retrieve.  

3. **Data Retrieval**:  
   - Provides tools (like queries) to fetch specific data quickly.  
   - Example: Searching for all students who scored above 90%.  

4. **Data Manipulation**:  
   - Allows users to insert, update, or delete data.  

5. **User Administration**:  
   - Controls who can access or modify data, ensuring security.  

---

#### **Functions of a DBMS**  
1. **Data Integrity**:  
   - Ensures data is accurate and consistent (e.g., no duplicate entries).  

2. **Concurrency Control**:  
   - Allows multiple users to access the database simultaneously without issues.  
   - Example: Two students registering for courses at the same time.  

3. **Backup and Recovery**:  
   - Protects data by saving backups and restoring it in case of failures.  

4. **Data Security**:  
   - Protects sensitive data by controlling access.  

5. **Scalability**:  
   - Can handle increasing amounts of data as businesses grow.  

---

#### **Examples of DBMS Software**  
1. **MySQL**: Popular for web applications.  
2. **Oracle DB**: Used by large enterprises for complex systems.  
3. **PostgreSQL**: Open-source and highly reliable.  
4. **Microsoft Access**: Simple databases for small businesses.  

---

### **Topic 7: Advantages of DBMS**  
DBMS offers several benefits over traditional file systems for managing data:
#### **1. Data Organization**  
- Data is stored in a structured format (tables, relationships), making it easy to access and manage.  
- Example: Retrieving customer purchase history in a few seconds.

#### **2. Data Integrity**  
- Ensures data remains accurate and consistent.  
- Example: If a student’s phone number is updated, it reflects across all related records.

#### **3. Concurrent Access**  
- Multiple users can access the database simultaneously without conflicts.  
- Example: Several employees in a company can work on the same database at once.

#### **4. Data Security**  
- Controls access to data and protects sensitive information.  
- Example: Only authorized users can access financial records in a banking system.

#### **5. Backup and Recovery**  
- Automatically creates backups and restores data after a failure.  
- Example: A DBMS recovers data after a power outage or system crash.

#### **6. Data Sharing**  
- Allows multiple users to access and share the same database.  
- Example: Departments in a company share customer and product information.

#### **7. Efficient Querying**  
- Powerful tools (like SQL) make it easy to retrieve and manipulate data.  
- Example: Generate a report of all sales in the last month with a single query.

--- 

### **Topic 8: Paradigm Shift from File System to DBMS (Hinglish)**  

Pehle ke zamaane mein, log **File Systems** ka use karte the data ko manage karne ke liye. Lekin file systems mein kuch problems thi, jo DBMS (Database Management System) ne solve ki. DBMS ek advanced tarika hai data ko organize aur manage karne ka.

---

#### **File System Issues (Problems with File Systems):**

1. **Data Redundancy (Data ka Repeat Hona)**  
   - File system mein data alag-alag jagah store hota tha, aur same data multiple files mein repeat hota tha.  
   - Example: Ek student ka phone number alag-alag departments (hostel, accounts) mein alag-alag jagah stored hota tha.

2. **Data Inconsistency (Mismatch in Data)**  
   - Agar ek jagah data update hota, to dusri jagah update nahi hota. Is wajah se mismatch create hota tha.  
   - Example: Accounts department mein phone number alag ho sakta hai aur hostel department mein alag.

3. **Difficult Data Access (Data Ko Dhoondhna Mushkil)**  
   - User ko pata hona chahiye ki file kahan hai aur manually search karna padta tha, jo time-consuming tha.  
   - Example: 10,000 students ke records mein ek student ka hostel number dhoondhna.

4. **Unauthorized Access (Security Ka Issue)**  
   - Kisi file ko access karna easy tha, jis wajah se sensitive data unauthorized users ke haath lag sakta tha.  
   - Example: Ek student apni marks file ko khud modify kar sakta tha.

5. **No Concurrent Access (Ek Time Par Sirf Ek User)**  
   - File system ek time par sirf ek user ko access allow karta tha. Multiple users ek saath kaam nahi kar sakte the.

6. **No Backup and Recovery**  
   - Agar file delete ya corrupt ho gayi, to koi backup ya recovery option nahi tha.  

---

#### **DBMS Advantages (DBMS Se File System Kaise Better Hai):**

1. **No Data Redundancy**  
   - Data centralized hota hai, aur repeat hone ka chance kam ho jata hai.  

2. **Data Consistency**  
   - Ek jagah data update hone par sabhi jagah same update hoti hai.  

3. **Easy Data Access**  
   - Queries (like SQL) ke through data easily retrieve kiya ja sakta hai.  
   - Example: Ek query likho aur instantly result mil jata hai.

4. **Secure Data**  
   - Access control aur user permissions ke zariye sensitive data ko protect kiya jata hai.  

5. **Concurrent Access**  
   - Multiple users ek hi time par data access aur modify kar sakte hain bina conflicts ke.  

6. **Backup and Recovery**  
   - System crash hone par data restore karne ka feature hota hai.

---

#### **Comparison Table: File System vs DBMS**

| **Feature**               | **File System**                               | **DBMS**                                   |
|---------------------------|-----------------------------------------------|-------------------------------------------|
| **Data Redundancy**       | High (same data stored in multiple places)    | Low (centralized storage reduces redundancy) |
| **Data Consistency**      | Difficult to maintain consistency             | Automatically maintains consistency        |
| **Data Access**           | Manual and slow                              | Fast and easy using queries like SQL       |
| **Security**              | Weak (no proper access control)              | Strong (user authentication and permissions) |
| **Concurrent Access**     | Not supported                                | Supported (multiple users access data simultaneously) |
| **Backup and Recovery**   | No built-in mechanism                        | Automated backup and recovery features     |
| **Ease of Use**           | Requires knowing file locations              | User-friendly with structured queries      |
| **Scalability**           | Difficult to handle large data               | Easily scalable for large datasets         |

---

#### **Conclusion (In Hinglish)**  
File System ek purani technology thi, jo chhoti applications ke liye sahi thi. Lekin DBMS ek modern approach hai jo bade data, security, aur performance issues ko solve karta hai. Aaj ke zamaane mein, DBMS preferred hai kyunki yeh fast, secure, aur efficient hai.




### **Topic 9: Structure of a DBMS**  

DBMS ka structure ek layered architecture par based hota hai jisme different components milkar data ko efficiently manage karte hain. Yeh components ek saath kaam karte hain taaki users ko reliable aur secure data management provide kiya ja sake.

---

### **Components of DBMS**

#### **1. Hardware**  
- Data ke liye jo physical devices use hote hain.  
- Example: Hard drives, SSDs, servers, network storage devices.  
- **Purpose**: Data ko store aur access karna.

---

#### **2. Software**  
- DBMS software ke alag-alag modules milkar pura system banate hain.  
- **Sub-components:**

1. **DBMS Engine**  
   - Core service jo database ke operations ko manage karta hai (e.g., storage, retrieval).

2. **Query Processor**  
   - Queries (like SQL) ko interpret aur execute karta hai.  
   - Example: Agar ek user "SELECT * FROM students" likhta hai, toh query processor iska result generate karega.

3. **Storage Manager**  
   - Data ko store, retrieve aur update karne ka kaam karta hai.  
   - Example: Tables, indexes, aur views ko manage karna.

4. **Transaction Manager**  
   - Ensure karta hai ki saare transactions ACID properties ko follow karein.  
   - Example: Agar ek transaction fail ho jaye, toh rollback karna.

5. **Concurrency Control Manager**  
   - Multiple users ke access ko handle karta hai bina kisi conflict ke.  
   - Example: Ek user data update kar raha ho aur doosra read kar raha ho, toh dono tasks smoothly honge.

6. **Recovery Manager**  
   - System crash hone par data ko restore karne ka kaam karta hai.  
   - Example: Logs aur checkpoints ka use karke database consistent state me wapas lata hai.

---

#### **3. Data**  
- Yeh database me stored actual data hai.  
- **Sub-components:**
  - **Database Schema**: Data ka logical structure define karta hai (e.g., tables, relationships).  
  - **Tables**: Rows aur columns me data store hota hai.  
  - **Indexes**: Data retrieval ko fast karte hain.  
  - **Views**: Virtual tables jo queries ke result ko represent karti hain.  

---

#### **4. Users**  
- DBMS ke saath kaam karne wale log aur applications.  
- **Types of Users:**
  1. **Database Administrators (DBAs)**  
     - Database ko manage aur secure karte hain.  
     - Example: Permissions set karna aur backup plan karna.
  2. **Developers**  
     - Applications likhte hain jo database ka use karti hain.  
     - Example: E-commerce application banane wale developers.
  3. **End Users**  
     - Applications ke zariye directly database ke saath interact karte hain.  
     - Example: Customers jo apne orders dekhte hain.

---

### **Topic 10 Architectural Layers of DBMS**  
DBMS ka architecture 3 layers me divided hai:

1. **External Level (User View Layer)**  
   - Users ka interaction yahan hota hai, jaise SQL queries likhna ya application ka use karna.  
   - Example: "SELECT * FROM students" likhne par result milega.

2. **Conceptual Level (Logical View Layer)**  
   - Pura database ka logical structure define karta hai, jaise tables aur relationships.  
   - Example: Students aur courses ke beech relationship define karna.

3. **Internal Level (Physical View Layer)**  
   - Data ka physical storage aur access ka method define karta hai.  
   - Example: Hard disk par data ko kaise store kiya jaye.

---

### **Interaction of Components**

1. **Query Execution**  
   - User ek query likhta hai, jo query processor ke through execute hoti hai aur result storage manager se retrieve hota hai.  
   - Example: "SELECT * FROM products" likhne par saari product details milti hain.

2. **Transaction Management**  
   - Transaction manager ensure karta hai ki transactions complete ya rollback ho.  
   - Example: Bank me ₹500 transfer karte time failure hone par rollback.

3. **Concurrency Control**  
   - Multiple transactions ko conflict-free execute karne ka kaam karta hai.  
   - Example: Ek user data update kar raha hai aur doosra read, toh dono smoothly kaam karte hain.

4. **Recovery**  
   - Recovery manager system failure ke baad consistent state restore karta hai.  
   - Example: Server crash hone ke baad database ka backup use karna.

---

#### **Conclusion**  
DBMS ka structure ek coordinated system hai jisme hardware, software, data, aur users milkar efficient aur secure data management provide karte hain. Har component ka apna specific role hai jo milkar ek reliable database environment banata hai.

---

### **Topic 9: Transaction Management in DBMS (Hinglish)**

Transaction Management DBMS ka ek important feature hai jo ensure karta hai ki database operations properly handle ho aur data consistent rahe. Ek **transaction** ka matlab hai ek group of operations (like insert, update, delete) jo ek unit ke taur par execute hoti hai. Agar koi operation fail ho jaye, to poori transaction rollback hoti hai, ensuring **data consistency**.

**Key Features:**  
- **Logically related operations**: Ek transaction ek ya zyada steps ka group hoti hai jo ek logical kaam ko complete karti hai, jaise ek bank account se paisa transfer karna.  
- **States**: Transaction ka execution multiple states se guzar kar hota hai.  
- **Consistency**: Ek transaction database ko ek consistent state se doosri consistent state mein le jati hai.  
- **ACID Properties**: Transactions ke specific rules hote hain jo database ki integrity aur reliability ko ensure karte hain.
---

#### **ACID Properties of Transactions**  
Transactions ke liye **ACID properties** ko follow karna zaroori hai:

1. **Atomicity (All or Nothing Rule)**  
   - **Explanation**: Ya to transaction ke saare operations complete honge ya phir koi bhi nahi. Agar koi operation fail ho, to poora transaction rollback ho jata hai.  
   - **Example**: Agar bank me ₹500 transfer karte ho aur beech me system crash ho jaye, to ya to poori amount transfer hogi, ya phir transaction cancel ho jayegi.

2. **Consistency**  
   - **Explanation**: Transaction ke baad database hamesha ek valid state me hona chahiye. Matlab data ke integrity constraints hamesha satisfy hone chahiye.  
   - **Example**: Agar ₹500 transfer hota hai, to ek account se deduct aur dusre account me add hona chahiye. Intermediate states invalid honge.

3. **Isolation**  
   - **Explanation**: Ek transaction ke operations doosri transactions ke operations ke saath interfere nahi karte. Parallel transactions properly handle ki jati hain.  
   - **Example**: Agar ek user account balance check kar raha hai aur doosra user simultaneously withdraw kar raha hai, dono operations alag-alag perform honge.

4. **Durability**  
   - **Explanation**: Jab ek transaction commit ho jati hai, uske changes permanent ho jate hain, even agar system crash ho jaye.  
   - **Example**: Agar ₹500 transfer successful hai, to system failure ke baad bhi dono accounts ka updated balance safe rahega.

---

#### **Key Components of Transaction Management**  
Transaction Management ke main parts jo ensure karte hain ki ACID properties maintain ho:

1. **Transaction Coordinator**  
   - Manage karta hai saare transactions aur ACID properties ka dhyan rakhta hai.  
   - Example: Decide karta hai ki transaction commit hoga ya rollback.

2. **Concurrency Control**  
   - Simultaneous transactions ke conflicts avoid karne ke liye mechanisms provide karta hai.  
   - Methods:  
     - **Locking**: Ek resource ko ek time par ek hi transaction access kar sakti hai.  
     - **Timestamp Ordering**: Transactions ke execution order ko timestamps ke through decide kiya jata hai.

3. **Recovery System**  
   - System failure ke baad database ko consistent state me wapas lane ke liye use hota hai.  
   - Techniques:  
     - **Logging**: Har transaction ka record rakha jata hai.  
     - **Checkpoints**: Periodic save points banaye jate hain jahan tak recovery ho sakti hai.

---

#### **Importance of Transaction Management**  
1. **Data Integrity Ensure Karna**: Har transaction ke baad data hamesha correct aur valid rahta hai.  
2. **Failure Handling**: Agar system crash ya error ho, to data loss ko prevent karta hai.  
3. **Simultaneous Access**: Multiple users ek saath database use kar sakte hain bina issues ke.  
4. **Reliable System**: Transaction management DBMS ko robust aur trustworthy banata hai.

---

#### **Real-Life Example (Hinglish)**  
- **Bank Transaction**:  
  Imagine karo ki tumne ₹500 ka transfer initiate kiya.  
  - **Atomicity** ensure karega ki ya to poora ₹500 transfer ho ya koi transaction na ho.  
  - **Consistency** dekhega ki source account se ₹500 deduct aur destination account me ₹500 add ho.  
  - **Isolation** ensure karega ki ek aur user ka withdrawal transaction tumhare transaction me interfere na kare.  
  - **Durability** ensure karega ki transfer commit hone ke baad system crash ho jaye to bhi ₹500 transfer ho chuka rahe.

Is tarah, transaction management database ko reliable aur efficient banata hai.

### **1. Operations of Transaction**  
Transactions ke andar alag-alag operations hote hain jo user ki request ke basis par perform hote hain:  

#### **i) Read(X)**  
- **Kya karta hai:** Database se kisi value ko read karne ka kaam karta hai aur usse memory buffer mein store karta hai.  
- **Kab hota hai:** Jab user sirf database ka content dekhna chahta hai bina koi changes kiye.  
- **Example:** Agar ek user apne bank account ka balance check karna chahta hai, toh system ek read operation perform karega aur balance user ko dikhayega.  
- **Samajhne ke liye:**  
  ``` 
  Read Operation: 
  - X = Account Balance
  - Value memory buffer mein store hoti hai.
  ```

#### **ii) Write(X)**  
- **Kya karta hai:** Database mein kisi naye ya updated value ko save karne ka kaam karta hai.  
- **Kaise hota hai:** Pehle ek read operation perform hota hai, fir memory buffer mein changes hote hain, aur uske baad write operation se final value database mein update hoti hai.  
- **Example:** Agar ek user apne account se ₹500 withdraw karta hai:  
  - Pehle account ka balance read hota hai.  
  - Us balance se ₹500 minus kiya jata hai.  
  - Phir write operation se updated balance database mein save hota hai.  
- **Samajhne ke liye:**  
  ``` 
  Read: X = 5000 (Account Balance)
  Update: X = 5000 - 500 (Withdrawn Amount)
  Write: Updated Balance = 4500
  ```

#### **iii) Commit**  
- **Kya karta hai:** Ye operation ensure karta hai ki ek transaction ke baad database consistent state mein ho.  
- **Importance:** Agar transaction ke beech koi failure ho jaye (power cut, software crash), toh commit se changes permanently save hote hain.  
- **Example:** Ek payment transaction complete hone ke baad commit operation karta hai, jisse paisa account se permanently deduct ho jata hai.  

#### **iv) Rollback**  
- **Kya karta hai:** Jab transaction ke beech mein failure ho jaye, toh rollback operation database ko uske last safe state mein le jata hai.  
- **Importance:** Ye database ko inconsistent state se bacha kar ek secure state mein rakhta hai.  
- **Example:** Agar ek transaction partially complete ho aur system crash ho jaye, toh rollback previous state ko restore karta hai.  

#### **Summary in Hinglish:**  
- **Read:** Data ko read karna.  
- **Write:** Data ko modify karke save karna.  
- **Commit:** Changes ko permanently apply karna.  
- **Rollback:** Failure hone par changes ko undo karna aur database ko previous state mein lana.

### **2. Transaction Schedules**  
Transaction schedule ka matlab hai transactions ke execute hone ka order. Jab ek time par multiple transactions execute hone ki demand hoti hai, toh unhe kaise execute karna hai, uska schedule banaya jata hai.  

#### **i) Serial Schedule (Sequential Execution)**  
- **Definition:** Is schedule mein ek waqt par sirf ek transaction execute hoti hai. Baaki sab transactions apni turn ka wait karti hain.  
- **Consistency:** Serial schedule hamisha database ko consistent rakhta hai kyunki ek transaction ke complete hone ke baad hi dusri transaction start hoti hai.  
- **Drawback:** Waiting time badh jata hai, system ka throughput (ek samay mein complete hone wali transactions) kam ho jata hai.  
- **Example:**  
  ``` 
  T1: Withdraw 500 from Account A
  T2: Deposit 500 in Account B
  Execution: 
  - T1 complete hoga pehle.
  - Phir T2 start hoga.
  ```

#### **ii) Non-Serial Schedule (Concurrent Execution)**  
- **Definition:** Isme multiple transactions ek saath execute hoti hain, ya ek transaction complete hone ke pehle hi doosri start ho jati hai.  
- **Efficiency:** Waiting time kam hota hai aur system ka throughput improve hota hai.  
- **Issue:** Inconsistency ka risk hota hai, agar proper concurrency control na ho.  
- **Example:**  
  ``` 
  T1: Read A, Update A
  T2: Read B, Update B
  Execution: T1 aur T2 ek saath chal sakti hain.
  ```

#### **Key Comparison:**  
| **Feature**           | **Serial Schedule** | **Non-Serial Schedule** |
|------------------------|---------------------|-------------------------|
| **Execution**          | Sequential          | Parallel/Concurrent     |
| **Consistency**        | Always maintained   | Depends on control      |
| **System Efficiency**  | Low                 | High                    |

---

### **3. Serializable Transactions**  
Serializable ka matlab hai ek non-serial schedule ko aise analyze karna ki kya wo database consistency ensure karega, jaise ek serial schedule karta hai.  

- **Kya hota hai:**  
  - Non-serial schedules me kabhi-kabhi parallel transactions ki wajah se conflicts ya errors ho sakte hain.  
  - Agar ek non-serial schedule ko kisi equivalent serial schedule me convert kiya ja sake aur wo database consistency maintain kare, toh usse **Serializable Schedule** kehte hain.  

#### **Types of Serializable Schedules:**  
1. **Conflict Serializable:**  
   - Agar non-serial schedule me conflicting operations ka order change karke serial schedule ban jaye, toh wo conflict serializable hota hai.  
   - **Example:**  
     ``` 
     T1: Read A → Write A
     T2: Read A → Write A
     Schedule: T1 → T2 (Serial form: No conflicts)
     ```

2. **View Serializable:**  
   - Isme focus hota hai ki final database ka result same ho, chahe schedule ka execution order different ho.  
   - Example ke liye, chahe T1 pehle chale ya T2, agar database ka final state same ho, toh wo view serializable hoga.  

#### **Why Serializable is Important?**  
- Non-serial schedules system efficiency improve karte hain, par conflicts ka risk hota hai.  
- Serializable property ensure karti hai ki database consistent state me hi rahega.  

---

#### **Summary in Hinglish:**  
- **Transaction Schedules:** Transactions ke execution ka order define karta hai.  
  - **Serial:** Ek time par ek transaction execute hoti hai, slow but consistent.  
  - **Non-Serial:** Multiple transactions ek saath execute hoti hain, fast but risk hota hai.  
- **Serializable Transactions:** Non-serial schedules jo consistency maintain karte hain jaise ek serial schedule, unhe serializable kehte hain.  
  - **Conflict Serializable:** Order adjust karne se consistency aaye.  
  - **View Serializable:** Final result same ho, chahe execution ka order alag ho.  

### **4. States of a Transaction in DBMS**  
Ek transaction ka execution alag-alag stages se guzar kar hota hai. In states ka purpose hota hai transaction ka status track karna aur database ki consistency ensure karna.

---

#### **i) Active State**  
- **Description:**  
  - Transaction shuru hoti hai aur operations perform kar rahi hoti hai.  
  - Yahan par data modify hota hai, par changes database mein abhi tak save nahi hote.  
- **Example:**  
  - Bank transaction ke time, jab withdrawal ya deposit process chal raha ho, tab transaction active state mein hoti hai.  
- **Key Point:**  
  - Agar failure ho jaye, toh transaction failed state mein chali jayegi.

---

#### **ii) Partially Committed State**  
- **Description:**  
  - Jab transaction apna last operation execute kar rahi hoti hai, par abhi tak commit nahi hua.  
  - Yahan par system check karta hai ki saari conditions meet ho rahi hain ya nahi.  
- **Example:**  
  - Ek balance update operation jab almost complete ho, par commit hone se pehle koi error aa jaye.  
- **Key Point:**  
  - Agar error aaye, toh rollback hoga; agar nahi, toh transaction committed state mein jayegi.

---

#### **iii) Committed State**  
- **Description:**  
  - Jab transaction successfully complete ho jaye aur saare changes database mein permanently save ho jayein.  
- **Example:**  
  - Bank account balance update hone ke baad naye balance ka save ho jaana.  
- **Key Point:**  
  - Ek bar transaction committed ho gayi, toh uske changes rollback nahi kiye ja sakte.

---

#### **iv) Failed State**  
- **Description:**  
  - Agar transaction ke beech koi error aa jaye, toh wo failed state mein chali jati hai.  
  - System ensure karta hai ki database inconsistent state mein na chhode.  
- **Example:**  
  - Agar withdrawal ke beech power failure ho jaye, toh transaction fail ho jayegi.  
- **Key Point:**  
  - Is state mein database ko last safe state tak le jane ke liye rollback hota hai.

---

#### **v) Aborted State**  
- **Description:**  
  - Jab transaction fail hone ke baad rollback ho jaye aur database ko uski last consistent state mein le jaya jaye.  
  - Recovery system transaction ko restart kar sakta hai ya completely terminate kar sakta hai.  
- **Example:**  
  - Withdrawal ke time system crash hone par database ko previous state mein wapas le aana.  
- **Key Point:**  
  - Transaction ya to dubara shuru hogi ya terminate.

---

#### **Transaction State Flow:**  
1. **Active → Partially Committed → Committed** (Successful completion)  
2. **Active → Failed → Aborted** (Failure recovery)  

---

#### **Summary in Hinglish:**  
- **Active:** Transaction chal rahi hai, data modify ho raha hai.  
- **Partially Committed:** Last operation chal raha hai, par commit abhi pending hai.  
- **Committed:** Transaction successfully complete, changes permanent ho gaye.  
- **Failed:** Error aane par transaction stop ho gayi.  
- **Aborted:** Transaction rollback ho gayi aur database safe state mein aa gaya.  