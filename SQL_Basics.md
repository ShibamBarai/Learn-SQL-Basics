### What is SQL?
SQL (Structured Query Language) is used to communicate with databases. It allows you to create, read, update, and delete data in a database (often referred to as CRUD operations).

### Basic Syntax
SQL commands are usually written in **uppercase**, but it’s case-insensitive (e.g., `SELECT` and `select` work the same). Commands end with a semicolon `;`.

### Let’s Begin with a Few Key Commands:

1. **SELECT**: Fetch data from a database.
2. **INSERT INTO**: Insert data into a table.
3. **UPDATE**: Update existing data.
4. **DELETE**: Delete data from a table.
5. **CREATE TABLE**: Create a new table.
6. **DROP TABLE**: Delete a table.

---

### 1. **SELECT**: Fetching Data from a Table

Imagine we have a table called `Employees`:

| EmployeeID | Name      | Age | Department |
|------------|-----------|-----|------------|
| 1          | John Doe  | 30  | Sales      |
| 2          | Jane Smith| 25  | Marketing  |
| 3          | Sam Brown | 40  | HR         |

To **select all columns** and rows:

```sql
SELECT * FROM Employees;
```

This would return:

| EmployeeID | Name      | Age | Department |
|------------|-----------|-----|------------|
| 1          | John Doe  | 30  | Sales      |
| 2          | Jane Smith| 25  | Marketing  |
| 3          | Sam Brown | 40  | HR         |

To **select specific columns**:

```sql
SELECT Name, Department FROM Employees;
```

Output:

| Name       | Department |
|------------|------------|
| John Doe   | Sales      |
| Jane Smith | Marketing  |
| Sam Brown  | HR         |

---

### 2. **INSERT INTO**: Adding Data

To add a new employee to the `Employees` table:

```sql
INSERT INTO Employees (EmployeeID, Name, Age, Department)
VALUES (4, 'Sara Green', 28, 'Finance');
```

---

### 3. **UPDATE**: Modifying Existing Data

Let’s say you want to update the department of 'John Doe' from `Sales` to `Management`:

```sql
UPDATE Employees
SET Department = 'Management'
WHERE Name = 'John Doe';
```

---

### 4. **DELETE**: Removing Data

To delete the employee 'Sara Green':

```sql
DELETE FROM Employees
WHERE Name = 'Sara Green';
```

---

### 5. **CREATE TABLE**: Creating a New Table

To create the `Employees` table:

```sql
CREATE TABLE Employees (
    EmployeeID INT,
    Name VARCHAR(50),
    Age INT,
    Department VARCHAR(50)
);
```

---

### 6. **DROP TABLE**: Deleting a Table

To delete the `Employees` table:

```sql
DROP TABLE Employees;
```

---

### Summary of SQL Basics:
- **SELECT**: Used to query data.
- **INSERT INTO**: Add data to tables.
- **UPDATE**: Change existing data.
- **DELETE**: Remove data.
- **CREATE TABLE**: Make new tables.
- **DROP TABLE**: Remove tables from a database.


### Key SQL Concepts We Will Cover Next:
1. **WHERE Clause**: Filtering data.
2. **ORDER BY**: Sorting data.
3. **JOIN**: Combining data from multiple tables.
4. **GROUP BY and Aggregations**: Summarizing data.
5. **ALTER TABLE**: Modifying an existing table.
6. **Constraints**: Enforcing rules on the data.
7. **SQL Functions**: Useful built-in functions.

---

### 1. **WHERE Clause**: Filtering Data
The `WHERE` clause is used to filter records that meet certain conditions.

Example: Find employees older than 30:

```sql
SELECT * FROM Employees
WHERE Age > 30;
```

---

### 2. **ORDER BY**: Sorting Data
`ORDER BY` is used to sort the result set in either ascending (`ASC`) or descending (`DESC`) order.

Example: Get all employees sorted by `Age` in descending order:

```sql
SELECT * FROM Employees
ORDER BY Age DESC;
```

---

### 3. **JOIN**: Combining Data from Multiple Tables
When your data is spread across multiple tables, you can use `JOIN` to combine them.

Imagine we have another table `Departments`:

| DepartmentID | DepartmentName |
|--------------|----------------|
| 1            | Sales          |
| 2            | Marketing      |
| 3            | HR             |
| 4            | Finance        |

To get the employee name along with the department name (combining `Employees` and `Departments` tables):

```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
JOIN Departments
ON Employees.Department = Departments.DepartmentID;
```

---

### 4. **GROUP BY and Aggregations**: Summarizing Data
`GROUP BY` allows you to group rows that have the same values into summary rows. It is often used with aggregation functions like `COUNT`, `AVG`, `SUM`, `MAX`, `MIN`.

Example: Find the average age of employees in each department:

```sql
SELECT Department, AVG(Age) AS AverageAge
FROM Employees
GROUP BY Department;
```

---

### 5. **ALTER TABLE**: Modifying an Existing Table
If you need to change the structure of an existing table, you can use `ALTER TABLE`.

Example: Add a new column `Salary` to the `Employees` table:

```sql
ALTER TABLE Employees
ADD Salary DECIMAL(10, 2);
```

---

### 6. **Constraints**: Enforcing Rules on Data
SQL allows you to apply constraints on columns to ensure data integrity. Common constraints include:
- **PRIMARY KEY**: Uniquely identifies each row in a table.
- **FOREIGN KEY**: Links two tables.
- **NOT NULL**: Ensures that a column cannot have a `NULL` value.
- **UNIQUE**: Ensures all values in a column are unique.
- **CHECK**: Ensures that all values in a column meet a specific condition.

Example: Define a `PRIMARY KEY` when creating a table:

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT,
    Department VARCHAR(50)
);
```

---

### 7. **SQL Functions**: Useful Built-in Functions
SQL provides many useful functions to manipulate data.

- **`COUNT()`**: Returns the number of rows.
- **`AVG()`**: Returns the average value.
- **`SUM()`**: Returns the sum of values.
- **`MIN()`** and **`MAX()`**: Return the smallest and largest values.

Example: Count the number of employees:

```sql
SELECT COUNT(*) FROM Employees;
```

---

### SQL Learning Roadmap:
1. **SQL Basics (What we've covered so far)**
2. **Data Filtering and Sorting**
3. **SQL Joins and Relationships**
4. **Aggregating and Grouping Data**
5. **Subqueries**
6. **Table Relationships and Foreign Keys**
7. **Advanced SQL Concepts (Views, Indexes, Transactions)**
8. **SQL Practice Resources**

---

### 1. **SQL Basics (Recap)**

- **SELECT**: Retrieves data from a table.
- **INSERT INTO**: Adds new data to the table.
- **UPDATE**: Modifies existing data.
- **DELETE**: Removes data.
- **CREATE TABLE**: Creates a new table.
- **DROP TABLE**: Deletes a table.

---

### 2. **Data Filtering and Sorting**

#### **WHERE Clause** (Filtering Data)
We use the `WHERE` clause to filter rows based on a condition. You can filter based on numbers, text, or comparisons.

Example: Find employees who are in the `HR` department:

```sql
SELECT * FROM Employees
WHERE Department = 'HR';
```

#### **Logical Operators** (`AND`, `OR`, `NOT`)
You can combine multiple conditions using logical operators:

Example: Find employees who are in the `HR` department and older than 30:

```sql
SELECT * FROM Employees
WHERE Department = 'HR' AND Age > 30;
```

Example: Find employees who are in the `HR` department or older than 40:

```sql
SELECT * FROM Employees
WHERE Department = 'HR' OR Age > 40;
```

#### **ORDER BY** (Sorting Data)
Sorting allows you to control how your results are displayed.

Example: Sort employees by `Age` in ascending order:

```sql
SELECT * FROM Employees
ORDER BY Age ASC;
```

To sort in descending order:

```sql
SELECT * FROM Employees
ORDER BY Age DESC;
```

---

### 3. **SQL Joins and Relationships**

#### **INNER JOIN** (Common Data Across Tables)
An `INNER JOIN` returns rows from both tables that match a condition.

Imagine two tables:
- `Employees` (Employee data)
- `Departments` (Department data)

```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.Department = Departments.DepartmentID;
```

This query joins `Employees` with `Departments` based on the `DepartmentID`, and returns only matching rows.

#### **LEFT JOIN** (All Records from Left Table)
A `LEFT JOIN` returns all rows from the left table (`Employees`), even if there’s no match in the right table (`Departments`).

```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.Department = Departments.DepartmentID;
```

---

### 4. **Aggregating and Grouping Data**

#### **GROUP BY**
`GROUP BY` allows you to group rows with similar values. It's used alongside aggregation functions like `COUNT()`, `SUM()`, `AVG()`.

Example: Count the number of employees in each department:

```sql
SELECT Department, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY Department;
```

#### **HAVING** (Filtering Grouped Data)
`HAVING` works like `WHERE` but is used to filter data after it's been grouped.

Example: Find departments with more than 2 employees:

```sql
SELECT Department, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 2;
```

---

### 5. **Subqueries** (Queries Inside Queries)

A **subquery** is a query nested inside another query. It is useful when you need to use the result of one query as a condition for another.

Example: Find the employees who are in the oldest department:

```sql
SELECT Name
FROM Employees
WHERE Department = (
    SELECT DepartmentID
    FROM Departments
    WHERE DepartmentName = 'HR'
);
```

---

### 6. **Table Relationships and Foreign Keys**

In relational databases, tables often reference each other. **Foreign keys** ensure that these relationships remain valid.

#### **Foreign Key**:
A foreign key in one table points to the primary key in another table, enforcing a relationship.

Example: Creating the `Employees` table with a foreign key referencing the `Departments` table:

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT,
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

This ensures that any value in the `DepartmentID` column of `Employees` must exist in the `Departments` table.

---

### 7. **Advanced SQL Concepts**

#### **Views** (Virtual Tables)
A **view** is a saved query that you can treat like a table. It doesn’t store data itself but dynamically generates it when queried.

Example: Create a view that shows employee names and their department names:

```sql
CREATE VIEW EmployeeDepartmentView AS
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
```

You can query the view like a regular table:

```sql
SELECT * FROM EmployeeDepartmentView;
```

#### **Indexes** (Speeding Up Queries)
An **index** is used to quickly find rows within a table. You can create an index on any column to speed up searches.

Example: Create an index on the `EmployeeID` column:

```sql
CREATE INDEX idx_employeeid ON Employees(EmployeeID);
```

#### **Transactions** (Managing Changes)
A **transaction** allows you to group multiple SQL operations into a single unit of work. If one operation fails, all changes can be rolled back.

Example: Start a transaction:

```sql
START TRANSACTION;

UPDATE Employees SET Salary = 50000 WHERE Name = 'John Doe';
DELETE FROM Employees WHERE Name = 'Jane Smith';

-- Commit changes
COMMIT;

-- Rollback changes if something goes wrong
-- ROLLBACK;
```

---


### 1. **SQL Basics** (Revisiting for Foundation)

- **Tables**: SQL works with tables that consist of rows and columns.
- **Datatypes**: Each column in a table has a specific data type, like `INT` (integer), `VARCHAR` (string), `DATE`, etc.

---

### 2. **Data Retrieval with SELECT and WHERE**

#### **SELECT**: Basic Data Retrieval
We use `SELECT` to retrieve specific columns or all columns from a table.

Example: Select all columns from the `Employees` table:

```sql
SELECT * FROM Employees;
```

To select specific columns (like `Name` and `Age`):

```sql
SELECT Name, Age FROM Employees;
```

#### **WHERE**: Filtering Data Based on Conditions
To filter data, use the `WHERE` clause.

Example: Select employees older than 30:

```sql
SELECT Name, Age FROM Employees
WHERE Age > 30;
```

You can filter by multiple conditions using `AND`/`OR`:

Example: Employees older than 30 and in the `Sales` department:

```sql
SELECT * FROM Employees
WHERE Age > 30 AND Department = 'Sales';
```

#### **LIKE** and Wildcards (`%` and `_`)
`LIKE` is used for pattern matching. `%` matches any sequence of characters, and `_` matches a single character.

Example: Find employees whose name starts with "J":

```sql
SELECT * FROM Employees
WHERE Name LIKE 'J%';
```

---

### 3. **Data Insertion and Modification**

#### **INSERT INTO**: Adding New Rows
To add new data to a table, use `INSERT INTO`.

Example: Add a new employee:

```sql
INSERT INTO Employees (EmployeeID, Name, Age, Department)
VALUES (5, 'Alice Johnson', 29, 'Marketing');
```

#### **UPDATE**: Modifying Existing Rows
The `UPDATE` command is used to modify data.

Example: Update the department of an employee:

```sql
UPDATE Employees
SET Department = 'Management'
WHERE Name = 'Alice Johnson';
```

#### **DELETE**: Removing Rows
`DELETE` is used to remove rows.

Example: Delete an employee by name:

```sql
DELETE FROM Employees
WHERE Name = 'Alice Johnson';
```

---

### 4. **Data Sorting and Limiting**

#### **ORDER BY**: Sorting Results
`ORDER BY` is used to sort data in ascending (`ASC`) or descending (`DESC`) order.

Example: Sort employees by `Age` in ascending order:

```sql
SELECT * FROM Employees
ORDER BY Age ASC;
```

Example: Sort employees by `Name` in descending order:

```sql
SELECT * FROM Employees
ORDER BY Name DESC;
```

#### **LIMIT**: Restricting Number of Rows
`LIMIT` allows you to control the number of rows returned.

Example: Get only the top 3 oldest employees:

```sql
SELECT * FROM Employees
ORDER BY Age DESC
LIMIT 3;
```

---

### 5. **SQL Joins and Relationships Between Tables**

In relational databases, you often have multiple related tables. **Joins** are used to combine data from two or more tables.

#### **INNER JOIN**: Matching Rows from Two Tables
An `INNER JOIN` returns rows from both tables only when there’s a match between them.

Imagine we have two tables:
- `Employees` (employee data)
- `Departments` (department data)

```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

This query retrieves employee names and the corresponding department names.

#### **LEFT JOIN**: Return All Rows from Left Table
A `LEFT JOIN` returns all rows from the left table (even if there’s no match in the right table).

```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

This will return all employees, even if they don’t have a corresponding department.

---

### 6. **Grouping and Aggregating Data**

#### **GROUP BY**: Grouping Rows Based on Columns
`GROUP BY` is used to group rows with the same values, often used with aggregation functions like `COUNT()`, `SUM()`, `AVG()`.

Example: Find the number of employees in each department:

```sql
SELECT Department, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY Department;
```

#### **HAVING**: Filtering Grouped Data
`HAVING` is like `WHERE`, but it filters after data is grouped.

Example: Find departments with more than 2 employees:

```sql
SELECT Department, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 2;
```

---

### 7. **Subqueries**: Queries Inside Queries

A **subquery** is a query inside another query. It’s useful when you need the result of one query as a condition for another.

#### **Simple Subquery**: 
Example: Find employees who work in the oldest department:

```sql
SELECT Name
FROM Employees
WHERE DepartmentID = (
    SELECT DepartmentID
    FROM Departments
    ORDER BY EstablishedYear ASC
    LIMIT 1
);
```

This subquery first finds the oldest department, and then the main query uses that result to fetch employees.

---

### 8. **Table Constraints**

Constraints ensure the integrity of the data in your tables. Common constraints include:

- **PRIMARY KEY**: Uniquely identifies each row.
- **FOREIGN KEY**: Enforces a relationship between two tables.
- **NOT NULL**: Ensures a column cannot be empty.
- **UNIQUE**: Ensures all values in a column are unique.
- **CHECK**: Ensures values meet specific conditions.

Example: Creating a table with constraints:

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Age INT CHECK (Age > 18),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

---

### 9. **Transactions**: Handling Multiple Operations Safely

A **transaction** groups multiple SQL operations into a single unit of work. If any operation fails, you can roll back all changes.

#### **BEGIN TRANSACTION** and **COMMIT**
Start a transaction and commit the changes:

```sql
START TRANSACTION;

UPDATE Employees SET Salary = 55000 WHERE EmployeeID = 1;
DELETE FROM Employees WHERE EmployeeID = 3;

COMMIT;
```

If something goes wrong, you can roll back the changes using `ROLLBACK`.

---

### 10. **Views**: Virtual Tables

A **view** is a saved query that can be treated like a table. It doesn’t store data itself, but it dynamically generates data when queried.

Example: Create a view of employee names and departments:

```sql
CREATE VIEW EmployeeDeptView AS
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
```

To query the view:

```sql
SELECT * FROM EmployeeDeptView;
```

---

### 11. **Indexes**: Speeding Up Data Retrieval

Indexes are used to improve the performance of queries. They allow the database to find data faster by indexing specific columns.

Example: Create an index on the `EmployeeID` column:

```sql
CREATE INDEX idx_employeeid ON Employees(EmployeeID);
```

---

### 12. **SQL Functions**

SQL has many built-in functions for manipulating and analyzing data.

- **`COUNT()`**: Returns the number of rows.
- **`SUM()`**: Returns the sum of a numeric column.
- **`AVG()`**: Returns the average value.
- **`MIN()` and `MAX()`**: Return the smallest and largest values.

Example: Find the total number of employees:

```sql
SELECT COUNT(*) FROM Employees;
```

Find the average employee age:

```sql
SELECT AVG(Age) FROM Employees;
```

---

### 13. **Advanced SQL: Window Functions**

Window functions allow you to perform calculations across a set of table rows related to the current row.

Example: Rank employees based on their salary:

```sql
SELECT Name, Salary,
RANK() OVER (ORDER BY Salary DESC) AS SalaryRank
FROM Employees;
```


### 14. **Set Operations** in SQL

Set operations are used to combine the results of two or more `SELECT` queries. The major set operations are:

- **UNION**: Combines the result of two queries and removes duplicates.
- **UNION ALL**: Combines the result of two queries but keeps duplicates.
- **INTERSECT**: Returns only the rows common to both queries.
- **EXCEPT**: Returns the rows from the first query that are not in the second query.

#### **UNION** Example:
Let's say we have two tables: `EmployeesUSA` and `EmployeesCanada`. To combine employees from both tables:

```sql
SELECT Name, Age FROM EmployeesUSA
UNION
SELECT Name, Age FROM EmployeesCanada;
```
This will return a combined list, with duplicates removed.

#### **UNION ALL** Example:
If you want to include duplicates:

```sql
SELECT Name, Age FROM EmployeesUSA
UNION ALL
SELECT Name, Age FROM EmployeesCanada;
```

#### **INTERSECT** Example:
To get employees common to both tables:

```sql
SELECT Name, Age FROM EmployeesUSA
INTERSECT
SELECT Name, Age FROM EmployeesCanada;
```

#### **EXCEPT** Example:
To get employees in the `EmployeesUSA` table but not in the `EmployeesCanada` table:

```sql
SELECT Name, Age FROM EmployeesUSA
EXCEPT
SELECT Name, Age FROM EmployeesCanada;
```

---

### 15. **SQL Constraints**

SQL constraints ensure the integrity and accuracy of the data in a database. Here are some commonly used constraints:

- **PRIMARY KEY**: Ensures that the column(s) uniquely identify each row.
- **FOREIGN KEY**: Ensures a valid relationship between two tables.
- **NOT NULL**: Ensures a column cannot have a NULL value.
- **UNIQUE**: Ensures all values in a column are different.
- **CHECK**: Ensures that all values in a column meet specific conditions.
- **DEFAULT**: Assigns a default value to a column if none is provided.

#### **Example of Constraints**:

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Age INT CHECK (Age > 18),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID),
    Email VARCHAR(100) UNIQUE,
    HireDate DATE DEFAULT CURRENT_DATE
);
```

This example includes:
- A **primary key** on `EmployeeID`.
- A **foreign key** referencing `Departments`.
- A **NOT NULL** constraint on `Name`.
- A **CHECK** constraint ensuring age is over 18.
- A **UNIQUE** constraint on the `Email` column.
- A **DEFAULT** constraint to automatically set the hire date to the current date.

---

### 16. **Advanced SQL Joins** (Beyond Inner and Left Joins)

There are several advanced ways to join data from multiple tables, each solving different data retrieval needs.

#### **RIGHT JOIN**:
Returns all rows from the right table and the matching rows from the left table.

Example: List all departments and their employees (even if some departments have no employees):

```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

#### **FULL OUTER JOIN**:
Returns all rows when there’s a match in either the left or right table. If there’s no match, it still returns rows with NULL values for unmatched rows.

Example: List all employees and departments, including departments with no employees and employees not assigned to a department:

```sql
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
FULL OUTER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

---

### 17. **Self Joins**

A **self join** is when a table is joined with itself. This is useful when you want to compare rows within the same table.

Example: Find employees who share the same manager (assuming a `ManagerID` column exists):

```sql
SELECT A.Name AS Employee, B.Name AS Manager
FROM Employees A
JOIN Employees B
ON A.ManagerID = B.EmployeeID;
```

This query creates two aliases (`A` and `B`) for the `Employees` table, and then joins the table to itself using the `ManagerID`.

---

### 18. **Recursive Queries Using Common Table Expressions (CTEs)**

A **Common Table Expression** (CTE) is a temporary result set that you can reference within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement.

#### **Example of a Basic CTE**:
This retrieves the names of employees and their departments:

```sql
WITH EmployeeDept AS (
    SELECT Employees.Name, Departments.DepartmentName
    FROM Employees
    JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID
)
SELECT * FROM EmployeeDept;
```

#### **Recursive CTE**:
Recursive CTEs are useful for hierarchical data (like an organizational chart).

Example: Find all employees in a hierarchy (where employees report to other employees):

```sql
WITH EmployeeHierarchy AS (
    SELECT EmployeeID, Name, ManagerID
    FROM Employees
    WHERE ManagerID IS NULL  -- Get top-level managers
    UNION ALL
    SELECT E.EmployeeID, E.Name, E.ManagerID
    FROM Employees E
    INNER JOIN EmployeeHierarchy EH ON E.ManagerID = EH.EmployeeID
)
SELECT * FROM EmployeeHierarchy;
```

---

### 19. **SQL Window Functions** (Advanced Analytics)

Window functions are powerful tools for performing calculations across a set of rows related to the current row. Unlike aggregate functions (`SUM()`, `COUNT()`), they don’t collapse rows into one.

#### **RANK()** Example:
Rank employees based on their salary:

```sql
SELECT Name, Salary, 
RANK() OVER (ORDER BY Salary DESC) AS SalaryRank
FROM Employees;
```

#### **ROW_NUMBER()** Example:
Assign a unique row number to each employee based on their hire date:

```sql
SELECT Name, HireDate, 
ROW_NUMBER() OVER (ORDER BY HireDate) AS RowNumber
FROM Employees;
```

#### **LEAD() and LAG()** Example:
Get the previous and next salary for each employee:

```sql
SELECT Name, Salary, 
LAG(Salary, 1) OVER (ORDER BY Salary) AS PreviousSalary,
LEAD(Salary, 1) OVER (ORDER BY Salary) AS NextSalary
FROM Employees;
```

These window functions allow you to perform complex analytics and comparisons without using subqueries or self-joins.

---

### 20. **Triggers**: Automating Actions in Databases

A **trigger** is a piece of code that is automatically executed in response to certain events on a table, such as `INSERT`, `UPDATE`, or `DELETE`.

#### **Example: Create a Trigger for Auditing**:
Let’s create a trigger that logs changes to the `Employees` table whenever an employee’s salary is updated.

```sql
CREATE TABLE EmployeeAudit (
    AuditID INT PRIMARY KEY AUTO_INCREMENT,
    EmployeeID INT,
    OldSalary DECIMAL(10, 2),
    NewSalary DECIMAL(10, 2),
    ChangeDate DATETIME
);

CREATE TRIGGER SalaryAudit
AFTER UPDATE ON Employees
FOR EACH ROW
BEGIN
    IF OLD.Salary != NEW.Salary THEN
        INSERT INTO EmployeeAudit (EmployeeID, OldSalary, NewSalary, ChangeDate)
        VALUES (NEW.EmployeeID, OLD.Salary, NEW.Salary, NOW());
    END IF;
END;
```

Now, every time an employee’s salary is updated, the old and new salaries are logged in the `EmployeeAudit` table.

---

### 21. **Stored Procedures**: Reusable SQL Code

A **stored procedure** is a set of SQL statements that you can save and reuse. You can think of them as functions that perform specific tasks.

#### **Creating a Stored Procedure**:
Let’s create a stored procedure to add a new employee:

```sql
CREATE PROCEDURE AddEmployee(
    IN empName VARCHAR(50),
    IN empAge INT,
    IN empDept INT
)
BEGIN
    INSERT INTO Employees (Name, Age, DepartmentID)
    VALUES (empName, empAge, empDept);
END;
```

You can now call this procedure instead of writing the `INSERT` statement each time:

```sql
CALL AddEmployee('John Smith', 30, 2);
```

Stored procedures allow you to bundle logic together and can greatly simplify repetitive tasks.

---

### 22. **User-Defined Functions (UDFs)**

A **user-defined function** is a custom function you create to perform a specific operation, similar to functions in programming languages.

#### **Example of a Scalar UDF**:
Create a function that calculates a yearly bonus based on salary:

```sql
CREATE FUNCTION CalculateBonus(salary DECIMAL(10, 2))
RETURNS DECIMAL(10, 2)
BEGIN
    RETURN salary * 0.10;  -- Bonus is 10% of salary
END;
```

You can now use this function in your queries:

```sql
SELECT Name, Salary, CalculateBonus(Salary) AS Bonus
FROM Employees;
```

---

### 23. **Normalization**: Organizing Data Efficiently

**Normalization** is the process of organizing data to reduce redundancy and improve data integrity. Here are the most common normal forms:

- **First Normal Form (1NF)**: Ensures that each column contains atomic (indivisible) values, and each column has a unique name.
- **Second Normal Form (

2NF)**: Ensures that all non-key attributes are fully dependent on the primary key.
- **Third Normal Form (3NF)**: Ensures that all non-key attributes are not only dependent on the primary key but also independent of each other.

#### **Example of 1NF**:
In a table, each cell must contain only one value. Consider an unnormalized table with multiple phone numbers in one cell:

| EmployeeID | Name  | PhoneNumbers      |
|------------|-------|-------------------|
| 1          | Alice | 123-456, 789-101  |

After 1NF, the table should look like this:

| EmployeeID | Name  | PhoneNumber |
|------------|-------|-------------|
| 1          | Alice | 123-456     |
| 1          | Alice | 789-101     |

---

### 24. **Best Practices for Writing Efficient SQL**

- **Use appropriate indexes** on columns that are frequently used in `WHERE` clauses or joins.
- **Avoid SELECT *:** Specify the columns you need to retrieve instead of selecting all columns.
- **Use JOINs instead of subqueries** whenever possible for better performance.
- **Optimize joins** by ensuring columns being joined are indexed.
- **Use `EXPLAIN`** to analyze how your query is being executed and identify potential inefficiencies.

---

### Practice and Learning Resources

1. **Interactive Learning Platforms:**
   - **W3Schools SQL Tutorial**: [W3Schools SQL](https://www.w3schools.com/sql/) - Great for beginners, offering explanations and an interactive SQL editor.
   - **SQLZoo**: [SQLZoo](https://sqlzoo.net/) - Has exercises with increasing difficulty to practice SQL queries.

2. **Hands-On SQL Practice:**
   - **LeetCode** (SQL section): [LeetCode SQL](https://leetcode.com/problemset/database/) - Offers SQL problems that you can solve directly on the platform.
   - **HackerRank** (SQL challenges): [HackerRank SQL](https://www.hackerrank.com/domains/tutorials/10-days-of-sql) - 10 days of SQL challenges to improve your skills.

3. **Further Reading:**
   - **Official SQL Documentation**: [SQL Tutorial](https://www.sqltutorial.org/) - A comprehensive guide with tutorials for all levels.
   - **SQLBook**: [SQLBook](https://www.sqlbook.com/) - Great for reference as you learn new SQL commands and concepts.
