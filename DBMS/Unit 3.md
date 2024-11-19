### **Relationship Algebra: Selection and Projection**

In relational database theory, **relational algebra** is a formal system used to manipulate and query relational data. **Selection** and **Projection** are two of the fundamental operations in relational algebra that are used to retrieve specific data from a relation (or table).

---

### **1. Selection (σ)**

#### **Definition:**
- **Selection** is used to filter the rows (tuples) in a table based on a given condition (predicate).
- It is represented as **σ(condition)(Relation)**, where `condition` is a logical expression, and `Relation` is the table.
- The selection operation returns only those rows from the table that satisfy the condition.

#### **Syntax in Relational Algebra:**
- `σ(condition)(R)` → Select rows from relation `R` that satisfy the `condition`.

#### **Example:**
Consider a table `Employees`:
| EmployeeID | Name      | Age | Department  |
|------------|-----------|-----|-------------|
| 1          | Alice     | 30  | HR          |
| 2          | Bob       | 24  | Engineering |
| 3          | Charlie   | 28  | HR          |
| 4          | David     | 34  | Engineering |

To select employees who are older than 30:
- `σ(Age > 30)(Employees)`

#### **SQL Query:**
```sql
SELECT * 
FROM Employees 
WHERE Age > 30;
```

This SQL query will return the employees whose `Age` is greater than 30.

---

### **2. Projection (π)**

#### **Definition:**
- **Projection** is used to retrieve only specific columns (attributes) from a table.
- It is represented as **π(attribute1, attribute2, ...)(Relation)**, where `attribute1`, `attribute2`, etc., are the columns to be selected, and `Relation` is the table.
- The projection operation removes duplicate rows and returns only the specified columns from the relation.

#### **Syntax in Relational Algebra:**
- `π(attribute1, attribute2, ...)(R)` → Project columns `attribute1`, `attribute2`, etc., from relation `R`.

#### **Example:**
Consider the same `Employees` table as above. To get the `Name` and `Department` of employees:
- `π(Name, Department)(Employees)`

#### **SQL Query:**
```sql
SELECT Name, Department
FROM Employees;
```

This SQL query will return the `Name` and `Department` columns for all employees.

---

### **Combining Selection and Projection**

You can combine both **Selection** and **Projection** to filter rows and select specific columns in a single operation.

#### **Example:**
If we want to select employees older than 30 and only display their `Name` and `Department`:
- **Relational Algebra**: `π(Name, Department)(σ(Age > 30)(Employees))`

#### **SQL Query:**
```sql
SELECT Name, Department
FROM Employees
WHERE Age > 30;
```

This SQL query will first filter the employees older than 30 and then display only their `Name` and `Department`.

---

### **Summary of Selection and Projection**

| **Operation**     | **Relational Algebra**      | **SQL Equivalent**                                        |
|-------------------|-----------------------------|-----------------------------------------------------------|
| **Selection**      | `σ(condition)(R)`            | `SELECT * FROM R WHERE condition;`                        |
| **Projection**     | `π(attribute1, ...)(R)`      | `SELECT attribute1, ... FROM R;`                          |
| **Combination**    | `π(attribute1, ...)(σ(condition)(R))` | `SELECT attribute1, ... FROM R WHERE condition;`  |

### **Example Walkthrough:**

- **Selection**:  
  If you have a table of employees and you want to find those who work in "Engineering", you would use **selection** to filter based on the department:
  
  Relational Algebra: `σ(Department = 'Engineering')(Employees)`  
  SQL:  
  ```sql
  SELECT * FROM Employees WHERE Department = 'Engineering';
  ```

- **Projection**:  
  If you only want to see the `Name` and `Age` of employees, use **projection**:
  
  Relational Algebra: `π(Name, Age)(Employees)`  
  SQL:  
  ```sql
  SELECT Name, Age FROM Employees;
  ```

- **Combination**:  
  To get the `Name` and `Age` of employees who are older than 30, you combine **selection** and **projection**:
  
  Relational Algebra: `π(Name, Age)(σ(Age > 30)(Employees))`  
  SQL:  
  ```sql
  SELECT Name, Age FROM Employees WHERE Age > 30;
  ```

---

### **Conclusion**

- **Selection** is used to filter rows based on a condition, and **Projection** is used to filter columns based on the attributes you need.
- Both operations are crucial in relational database queries and are directly translatable into SQL commands for practical usage.

---

### **Set Operations in SQL**

Set operations allow you to combine results from two or more SQL queries. These operations are based on mathematical set theory, and they include **Union**, **Intersection**, **Difference**, and **Symmetric Difference**. These operations are used to manipulate data that come from multiple tables or queries, and they rely on the idea of combining results that satisfy certain conditions.

### **1. UNION**

#### **Definition:**
- The **`UNION`** operator combines the result sets of two or more `SELECT` queries into a single result set.
- It **removes duplicates** by default, meaning it only returns unique rows.
- The queries must return the same number of columns, and the columns must have compatible data types.

#### **Example:**
Assume you have two tables, `Employees` and `Contractors`, both with columns `Name` and `Department`.

**SQL Query (UNION):**
```sql
SELECT Name, Department FROM Employees
UNION
SELECT Name, Department FROM Contractors;
```

This query will return a list of all unique `Name` and `Department` combinations from both `Employees` and `Contractors` tables.

#### **Note:**
- If you want to include duplicates, you can use `UNION ALL` instead of just `UNION`.

**SQL Query (UNION ALL):**
```sql
SELECT Name, Department FROM Employees
UNION ALL
SELECT Name, Department FROM Contractors;
```

---

### **2. INTERSECT**

#### **Definition:**
- The **`INTERSECT`** operator returns only the rows that exist in both `SELECT` queries.
- It returns the **common rows** between the two result sets.

#### **Example:**
If you want to find the employees and contractors who are working in the **same department**:

**SQL Query (INTERSECT):**
```sql
SELECT Name, Department FROM Employees
INTERSECT
SELECT Name, Department FROM Contractors;
```

This query will return a list of `Name` and `Department` combinations that are common between `Employees` and `Contractors`.

---

### **3. EXCEPT (or MINUS)**

#### **Definition:**
- The **`EXCEPT`** (or **`MINUS`** in some databases like Oracle) operator returns the rows from the first query that do not exist in the second query.
- It essentially performs a **difference** operation between the two result sets.

#### **Example:**
If you want to find employees who are **not contractors**:

**SQL Query (EXCEPT):**
```sql
SELECT Name, Department FROM Employees
EXCEPT
SELECT Name, Department FROM Contractors;
```

This query will return the `Name` and `Department` combinations that are present in the `Employees` table but not in the `Contractors` table.

#### **Note:**
- In Oracle, the operator is `MINUS` instead of `EXCEPT`.

---

### **4. SYMMETRIC DIFFERENCE**

#### **Definition:**
- The **`SYMMETRIC DIFFERENCE`** (often implemented as a combination of `UNION` and `EXCEPT`) returns the rows that exist in **either of the result sets but not in both**.
- SQL does not have a direct `SYMMETRIC DIFFERENCE` operator, but you can achieve it by using a combination of `UNION` and `EXCEPT`.

#### **Example:**
To find rows that are in either `Employees` or `Contractors`, but **not both**:

**SQL Query (SYMMETRIC DIFFERENCE):**
```sql
(SELECT Name, Department FROM Employees
EXCEPT
SELECT Name, Department FROM Contractors)
UNION
(SELECT Name, Department FROM Contractors
EXCEPT
SELECT Name, Department FROM Employees);
```

This query first returns rows from `Employees` not in `Contractors` and then adds rows from `Contractors` not in `Employees`, effectively giving you the symmetric difference.

---

### **Summary of Set Operations**

| **Operation**      | **Description**                                         | **SQL Example**                                        |
|--------------------|---------------------------------------------------------|--------------------------------------------------------|
| **UNION**          | Combines results from two queries, removing duplicates | `SELECT Name, Department FROM Employees UNION SELECT Name, Department FROM Contractors;` |
| **UNION ALL**      | Combines results from two queries, including duplicates | `SELECT Name, Department FROM Employees UNION ALL SELECT Name, Department FROM Contractors;` |
| **INTERSECT**      | Returns only the rows that are common to both queries  | `SELECT Name, Department FROM Employees INTERSECT SELECT Name, Department FROM Contractors;` |
| **EXCEPT**         | Returns rows from the first query that are not in the second query | `SELECT Name, Department FROM Employees EXCEPT SELECT Name, Department FROM Contractors;` |
| **SYMMETRIC DIFFERENCE** | Returns rows in either of the two result sets, but not in both | `(SELECT Name, Department FROM Employees EXCEPT SELECT Name, Department FROM Contractors) UNION (SELECT Name, Department FROM Contractors EXCEPT SELECT Name, Department FROM Employees);` |

---

### **Key Points to Remember:**
- **UNION** removes duplicates; use `UNION ALL` if duplicates are needed.
- **INTERSECT** finds the common rows between two queries.
- **EXCEPT** (or `MINUS` in Oracle) returns rows in the first query but not the second.
- **SYMMETRIC DIFFERENCE** returns rows that are in one of the queries but not both (achieved through a combination of `UNION` and `EXCEPT`).

These set operations provide powerful tools for querying and combining data in a relational database.

### **Renaming in Relational Algebra and SQL**

**Renaming** is the process of giving an alias or alternative name to a relation (table) or its attributes (columns) in both relational algebra and SQL. This is useful for simplifying queries, especially when dealing with multiple instances of the same table or when making the output more readable.

---

### **Renaming in Relational Algebra**

In **relational algebra**, renaming is performed using the **ρ (rho) operator**. The renaming operator changes the name of a relation or an attribute.

#### **1. Renaming a Relation:**
You can rename a relation by using the following syntax:
- **ρ(new_relation_name)(R)**  
  Where `new_relation_name` is the new name for the relation `R`.

#### **Example:**
If you have a relation (table) `Employees` and you want to rename it to `Staff`, you would use:
- **ρ(Staff)(Employees)**

#### **2. Renaming Attributes:**
You can also rename the attributes (columns) of a relation. The syntax is:
- **ρ(new_attribute_name1, new_attribute_name2, ...)(R)**  
  Where `new_attribute_name1`, `new_attribute_name2`, etc., are the new names for the attributes in relation `R`.

#### **Example:**
If you have a relation `Employees(Name, Age)` and you want to rename `Name` to `EmployeeName` and `Age` to `EmployeeAge`, you would use:
- **ρ(EmployeeName, EmployeeAge)(Employees)**

---

### **Renaming in SQL**

In **SQL**, renaming is typically done using the **`AS`** keyword in `SELECT` statements, which creates an alias for a column or table.

#### **1. Renaming Columns:**
You can rename columns in the output of a query using `AS`. This does not affect the actual table but changes the column name in the result set.

#### **Syntax:**
```sql
SELECT column_name AS new_column_name
FROM table_name;
```

#### **Example:**
If you want to rename the `Name` column to `EmployeeName` in the result of a query:
```sql
SELECT Name AS EmployeeName
FROM Employees;
```

#### **2. Renaming Tables (Table Alias):**
You can also give an alias to a table using the `AS` keyword in `FROM` or `JOIN` clauses. This is particularly useful for queries with joins or when using the same table multiple times.

#### **Syntax:**
```sql
SELECT column_name
FROM table_name AS alias_name;
```

#### **Example:**
If you want to rename the `Employees` table to `E` for convenience:
```sql
SELECT Name, Age
FROM Employees AS E;
```

---

### **Renaming in SQL with Multiple Tables (Joins)**

Renaming tables using aliases is especially helpful in joins where you might have multiple instances of the same table in the query.

#### **Example with JOIN:**
Assume you have two tables: `Employees` and `Departments`. You want to join them and use aliases to refer to them:
```sql
SELECT E.Name, D.DepartmentName
FROM Employees AS E
JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID;
```

In this example:
- `E` is an alias for the `Employees` table.
- `D` is an alias for the `Departments` table.

---

### **Summary of Renaming:**

| **Operation**           | **Relational Algebra**                          | **SQL**                                      |
|-------------------------|-------------------------------------------------|----------------------------------------------|
| **Rename Relation**      | ρ(new_relation_name)(R)                        | Not directly supported; done through aliases in queries. |
| **Rename Attribute**      | ρ(new_attribute_name1, new_attribute_name2)(R)  | `SELECT column_name AS new_column_name FROM table_name;` |
| **Table Alias**          | Not directly supported                         | `FROM table_name AS alias_name`              |

Renaming in SQL is more flexible and widely used for clarifying or simplifying queries, especially in complex queries involving multiple tables or when you need more readable column names in the results.

---

### **Joins in Relational Algebra and SQL**

A **join** combines rows from two or more relations (tables) based on a related column. Joins are essential for querying databases where data is stored across multiple tables.

---

### **1. Types of Joins in Relational Algebra**

In **relational algebra**, joins are a combination of different types of operations, such as **Cartesian Product**, **Selection**, and **Projection**.

#### **a. Theta Join (θ-Join)**
A **theta join** is a join where a condition (theta) is applied between two relations. The condition can be any arbitrary predicate.

**Syntax:**
- **R ⨝θ S**

Where:
- `R` and `S` are two relations.
- `θ` is a condition (e.g., `=`, `<`, `>`, etc.).

#### **Example:**
If you want to join two relations, `Employees(EmployeeID, Name)` and `Departments(DepartmentID, DeptName)` on the condition that the `DepartmentID` of `Employees` matches the `DepartmentID` in `Departments`:

- **Employees ⨝θ (Employees.DepartmentID = Departments.DepartmentID) Departments**

#### **b. Natural Join**
A **natural join** is a special case of the theta join where the condition is that attributes with the same name in both relations are used as the join condition. It combines rows where values of these attributes match.

**Syntax:**
- **R ⨝ S**

Where:
- The columns with the same name in both `R` and `S` are used as the join condition.

#### **Example:**
If `Employees(EmployeeID, DepartmentID)` and `Departments(DepartmentID, DeptName)` have a common `DepartmentID`, the natural join would automatically join them on `DepartmentID`:

- **Employees ⨝ Departments**

This would result in a table that includes `EmployeeID`, `DepartmentID`, and `DeptName`.

#### **c. Equi Join**
An **equi join** is a special case of the theta join where the condition is specifically an equality (`=`).

**Syntax:**
- **R ⨝θ (R.attribute = S.attribute) S**

Where the condition is equality.

#### **Example:**
- **Employees ⨝θ (Employees.DepartmentID = Departments.DepartmentID) Departments**

---

### **2. Joins in SQL**

In **SQL**, joins are used to combine rows from two or more tables based on a related column. The most commonly used joins are **INNER JOIN**, **LEFT JOIN**, **RIGHT JOIN**, and **FULL OUTER JOIN**.

#### **a. INNER JOIN**
The **`INNER JOIN`** returns only the rows where there is a match in both tables.

**SQL Syntax:**
```sql
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

#### **Example:**
If you have the `Employees` and `Departments` tables, and you want to find the employees along with their department names, you would use:

```sql
SELECT Employees.EmployeeID, Employees.Name, Departments.DeptName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

#### **b. LEFT JOIN (or LEFT OUTER JOIN)**
The **`LEFT JOIN`** returns all rows from the left table (table1), and the matched rows from the right table (table2). If there is no match, `NULL` values are returned for columns from the right table.

**SQL Syntax:**
```sql
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```

#### **Example:**
```sql
SELECT Employees.EmployeeID, Employees.Name, Departments.DeptName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

#### **c. RIGHT JOIN (or RIGHT OUTER JOIN)**
The **`RIGHT JOIN`** works the same as the `LEFT JOIN`, but it returns all rows from the right table, and the matched rows from the left table.

**SQL Syntax:**
```sql
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```

#### **d. FULL OUTER JOIN**
The **`FULL OUTER JOIN`** returns all rows when there is a match in either table. If no match is found, `NULL` values are returned for columns from the table that does not have a match.

**SQL Syntax:**
```sql
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

---

### **3. Division in Relational Algebra**

**Division** in relational algebra is used when you need to find all the rows from one relation that match all rows in another relation. This is often used for **"for all"** queries.

#### **Syntax:**
- **R ÷ S**

Where `R` is the relation to divide, and `S` is the relation that defines the criteria.

#### **Example:**
Consider two relations:
- `Students(StudentID, CourseID)`
- `Courses(CourseID)`

If you want to find students who have taken **all courses** listed in the `Courses` table, you would use division:

**SQL Equivalent:**
```sql
SELECT StudentID
FROM Students
WHERE NOT EXISTS (
    SELECT CourseID
    FROM Courses
    WHERE NOT EXISTS (
        SELECT 1
        FROM Students
        WHERE Students.StudentID = StudentID
        AND Students.CourseID = Courses.CourseID
    )
);
```

This query finds the `StudentID` for students who have enrolled in every course listed in the `Courses` table.

---

### **4. Tuple Relational Calculus (TRC)**

**Tuple Relational Calculus** (TRC) is a declarative language for querying relational databases, similar to SQL but with a more mathematical foundation. It allows for expressing queries in terms of what should be retrieved rather than how.

#### **Syntax of TRC:**
- A query in TRC takes the form:  
  `{T | P(T)}`  
  Where:
  - `T` is a tuple variable (like a row in a table).
  - `P(T)` is the condition that must hold for the tuple `T` to be included in the result set.

#### **Example:**
To retrieve the names of employees who are in a specific department:

**TRC Query:**
```text
{T.Name | ∃D (Employees(T) ∧ Departments(D) ∧ T.DepartmentID = D.DepartmentID ∧ D.DeptName = 'Sales')}
```
This query retrieves the `Name` of all employees who work in the 'Sales' department.

---

### **5. Domain Relational Calculus (DRC)**

**Domain Relational Calculus** (DRC) is another variant of relational calculus. It uses domain variables that range over individual attributes rather than entire tuples.

#### **Syntax of DRC:**
- A query in DRC takes the form:  
  `{D1, D2, ..., Dn | P(D1, D2, ..., Dn)}`  
  Where:
  - `D1, D2, ..., Dn` are domain variables.
  - `P(D1, D2, ..., Dn)` is the condition.

#### **Example:**
To retrieve the `Name` and `DepartmentID` of employees in the 'Sales' department:

**DRC Query:**
```text
{E.Name, E.DepartmentID | ∃D (Employees(E) ∧ D.DeptName = 'Sales' ∧ E.DepartmentID = D.DepartmentID)}
```

This query retrieves the `Name` and `DepartmentID` of employees who are in the 'Sales' department.

---

### **Summary of Key Concepts:**

| **Concept**          | **Description**                                                                 | **Relational Algebra**                               | **SQL**                                              |
|----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------|------------------------------------------------------|
| **Join**             | Combines rows from two or more tables based on a related column.                 | Theta Join, Natural Join, Equi Join, etc.           | INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN   |
| **Division**         | Finds rows in one relation that match all rows in another relation.              | `R ÷ S`                                             | Using subqueries with `NOT EXISTS` in SQL            |
| **Tuple Relational Calculus** (TRC) | Queries are based on conditions over tuples.                              | `{T | P(T)}`                                        | Similar to SQL but more declarative                  |
| **Domain Relational Calculus** (DRC) | Queries use domain variables to retrieve specific attributes.           | `{D1, D2, ..., Dn | P(D1, D2, ..., Dn)}`           | Similar to SQL with specific variable conditions      |

These concepts are essential for understanding how relational data can be queried, manipulated, and combined in a database system.

### **Expressive Power of Relational Algebra and Relational Calculus**

The **expressive power** of a query language refers to the range of queries or operations that can be expressed using that language. In the context of relational databases, **relational algebra** and **relational calculus** are two formal query languages used to manipulate and retrieve data from relational databases.

Both of these query languages are based on set theory and predicate logic, but they differ in how they express queries.

---

### **1. Relational Algebra**

**Relational Algebra** is a procedural query language, meaning that it specifies a series of operations to be performed on the data. The operations are **set-based** and manipulate relations (tables). The key operations in relational algebra are:

- **Selection (σ)**: Selects rows based on a condition.
- **Projection (π)**: Selects columns (attributes).
- **Union (∪)**: Combines the results of two queries, excluding duplicates.
- **Difference (−)**: Retrieves rows that are in one relation but not in the other.
- **Cartesian Product (×)**: Combines two relations in all possible ways.
- **Join (⨝)**: Combines two relations based on a condition (like matching attributes).
- **Rename (ρ)**: Renames a relation or an attribute.

#### **Expressive Power of Relational Algebra:**
Relational algebra can express a variety of queries and is often used as a foundation for understanding query optimization in relational database systems. While relational algebra is **procedural**, meaning it specifies **how** to get the result, it is not as flexible as relational calculus in terms of expressing queries.

- **Join and Union Operations**: These are powerful and can handle many kinds of queries.
- **Limited by Procedural Nature**: It may require complex combinations of operations (e.g., join, projection) to express certain queries.
  
#### **Example of Relational Algebra Query:**
To find the names of employees who work in the 'Sales' department:
```plaintext
π Name (σ DeptName='Sales' (Employees ⨝ Departments))
```
This query performs the following:
- Join `Employees` with `Departments` on a common attribute.
- Select the rows where the `DeptName` is 'Sales'.
- Project the `Name` attribute.

---

### **2. Relational Calculus**

**Relational Calculus** is a declarative query language. Unlike relational algebra, it does not specify the **how** of the query execution but instead focuses on describing **what** the result should be. There are two types of relational calculus:

- **Tuple Relational Calculus (TRC)**: In TRC, queries are expressed in terms of **tuples** (rows) of a relation.
- **Domain Relational Calculus (DRC)**: In DRC, queries are expressed in terms of **attributes** (columns) rather than tuples.

#### **Expressive Power of Relational Calculus:**
Relational calculus is more **expressive** than relational algebra because it allows a more natural and flexible way to specify queries, particularly when dealing with complex conditions or aggregates. It is more **closely aligned with declarative SQL**, where you specify the result without caring about the execution details.

- **Flexibility**: Relational calculus can express queries in a more abstract, flexible, and intuitive manner.
- **Declarative Nature**: It is more powerful than relational algebra for expressing certain types of queries.
- **Can Express More Complex Queries**: Relational calculus allows for the expression of queries with multiple conditions, negations, and existential quantifiers.

#### **Example of Relational Calculus Query (Tuple Relational Calculus):**
To retrieve the names of employees who work in the 'Sales' department:
```plaintext
{ T.Name | ∃ D (Employees(T) ∧ Departments(D) ∧ T.DepartmentID = D.DepartmentID ∧ D.DeptName = 'Sales') }
```
This query specifies:
- A tuple `T` from `Employees` and a tuple `D` from `Departments`.
- The join condition: `T.DepartmentID = D.DepartmentID`.
- The condition: `D.DeptName = 'Sales'`.
- The result: The `Name` of employees who satisfy this condition.

#### **Example of Relational Calculus Query (Domain Relational Calculus):**
```plaintext
{ E.Name | ∃ D (Employees(E) ∧ Departments(D) ∧ E.DepartmentID = D.DepartmentID ∧ D.DeptName = 'Sales') }
```
This query is similar to the tuple query but uses domain variables.

---

### **Comparison of Relational Algebra and Relational Calculus**

| **Aspect**             | **Relational Algebra**                                  | **Relational Calculus**                                   |
|------------------------|----------------------------------------------------------|-----------------------------------------------------------|
| **Type**               | Procedural query language (specifies how to retrieve data) | Declarative query language (specifies what data to retrieve) |
| **Flexibility**        | Less flexible; requires combining operations to express complex queries | More flexible; can express complex conditions naturally   |
| **Ease of Use**        | More difficult to write complex queries (requires multiple operations) | Easier for expressing complex queries (uses logical conditions) |
| **Declarative Nature** | Not declarative; specifies the steps of execution      | Declarative; focuses on the result, not the execution steps |
| **Expressiveness**     | Less expressive compared to relational calculus        | More expressive, can handle more complex queries          |
| **SQL Equivalence**    | SQL is closer to relational algebra in terms of operations | SQL is closer to relational calculus in its declarative style |

---

### **Example Queries Comparing Algebra and Calculus:**

#### **Relational Algebra Example:**
Find employees who work in 'Sales' department:
```plaintext
π Name (σ DeptName='Sales' (Employees ⨝ Departments))
```

#### **Tuple Relational Calculus Example:**
```plaintext
{ T.Name | ∃ D (Employees(T) ∧ Departments(D) ∧ T.DepartmentID = D.DepartmentID ∧ D.DeptName = 'Sales') }
```

#### **Domain Relational Calculus Example:**
```plaintext
{ E.Name | ∃ D (Employees(E) ∧ Departments(D) ∧ E.DepartmentID = D.DepartmentID ∧ D.DeptName = 'Sales') }
```

In these examples:
- **Relational Algebra** requires joining the tables and then selecting and projecting.
- **Tuple Relational Calculus** focuses on the tuples and uses existential quantifiers to express the conditions.
- **Domain Relational Calculus** focuses on attributes (columns) and uses domain variables to express the condition.

---

### **Conclusion:**
- **Relational Algebra** is more procedural and requires explicitly describing the steps to achieve the result. It is powerful but less flexible than relational calculus.
- **Relational Calculus** (both TRC and DRC) is more flexible and declarative, providing a more natural way to express complex queries. It is more **expressive** than relational algebra, particularly for queries that involve multiple conditions, negations, or complex relationships between data.

Both relational algebra and relational calculus are foundational to understanding SQL, but relational calculus is generally considered more expressive due to its declarative nature.