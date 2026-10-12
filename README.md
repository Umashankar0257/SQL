# SQL INTERVIEW PREPARATION
## Azure Data Engineer | Data Engineer | SQL Developer

> Complete SQL theory + query preparation guide for technical interviews.
>
> Focus: SQL fundamentals, joins, subqueries, correlated subqueries, CTEs,
> window functions, transactions, ACID, indexing, concurrency, optimization,
> 100 interview questions and Data Engineer scenario-based questions.

---

# TABLE OF CONTENTS

- [1. SQL Fundamentals](#1-sql-fundamentals)
- [2. SQL Command Types](#2-sql-command-types)
- [3. Keys and Constraints](#3-keys-and-constraints)
- [4. Joins](#4-joins)
- [5. Aggregations](#5-aggregations)
- [6. Subqueries](#6-subqueries)
- [7. Correlated Subqueries](#7-correlated-subqueries)
- [8. CTE](#8-cte)
- [9. Recursive CTE](#9-recursive-cte)
- [10. Window Functions](#10-window-functions)
- [11. NULL Handling](#11-null-handling)
- [12. CASE](#12-case)
- [13. Set Operators](#13-set-operators)
- [14. Date and String Functions](#14-date-and-string-functions)
- [15. Duplicate Handling](#15-duplicate-handling)
- [16. Transactions](#16-transactions)
- [17. ACID Properties](#17-acid-properties)
- [18. Concurrency](#18-concurrency)
- [19. Isolation Levels](#19-isolation-levels)
- [20. Locks](#20-locks)
- [21. Deadlocks](#21-deadlocks)
- [22. Indexing](#22-indexing)
- [23. Normalization](#23-normalization)
- [24. OLTP vs OLAP](#24-oltp-vs-olap)
- [25. Query Execution Order](#25-query-execution-order)
- [26. Query Optimization](#26-query-optimization)
- [27. 100 SQL Interview Questions](#27-100-sql-interview-questions)
- [28. Data Engineer Scenario Questions](#28-data-engineer-scenario-questions)
- [29. Final Revision Checklist](#29-final-revision-checklist)

---
Yes — you are asking for the **actual ready-to-paste `README.md` source code**, not just the content.

The previous response was formatted as Markdown, but if you want to put it directly into GitHub, do this:

1. Create a file named **`README.md`**
2. Open it in VS Code / Notepad
3. Paste the complete code below
4. Save it
5. Push it to GitHub

Because the complete SQL guide is large, I recommend making the README itself a **revision handbook**, with every topic having **Theory → Example → Interview Question → Answer → Query**.

Here is the proper structure I recommend for your repository:

```text
SQL-INTERVIEW-PREPARATION/
│
├── README.md                  ← Main revision handbook
│
├── 01-Basics/
├── 02-Joins/
├── 03-Aggregations/
├── 04-Subqueries/
├── 05-CTE/
├── 06-Window-Functions/
├── 07-Advanced-SQL/
├── 08-Transactions/
├── 09-Indexing/
├── 10-Concurrency/
├── 11-Query-Optimization/
├── 12-SQL-100-Questions/
└── 13-Scenario-Based/
```

But since you specifically want **everything in one README for revision**, your `README.md` should look like this:

```markdown
# SQL INTERVIEW PREPARATION
## Azure Data Engineer | Data Engineer | SQL Developer

> Complete SQL theory + query preparation guide for technical interviews.
>
> Focus: SQL fundamentals, joins, subqueries, correlated subqueries, CTEs,
> window functions, transactions, ACID, indexing, concurrency, optimization,
> 100 interview questions and Data Engineer scenario-based questions.

---

# TABLE OF CONTENTS

- [1. SQL Fundamentals](#1-sql-fundamentals)
- [2. SQL Command Types](#2-sql-command-types)
- [3. Keys and Constraints](#3-keys-and-constraints)
- [4. Joins](#4-joins)
- [5. Aggregations](#5-aggregations)
- [6. Subqueries](#6-subqueries)
- [7. Correlated Subqueries](#7-correlated-subqueries)
- [8. CTE](#8-cte)
- [9. Recursive CTE](#9-recursive-cte)
- [10. Window Functions](#10-window-functions)
- [11. NULL Handling](#11-null-handling)
- [12. CASE](#12-case)
- [13. Set Operators](#13-set-operators)
- [14. Date and String Functions](#14-date-and-string-functions)
- [15. Duplicate Handling](#15-duplicate-handling)
- [16. Transactions](#16-transactions)
- [17. ACID Properties](#17-acid-properties)
- [18. Concurrency](#18-concurrency)
- [19. Isolation Levels](#19-isolation-levels)
- [20. Locks](#20-locks)
- [21. Deadlocks](#21-deadlocks)
- [22. Indexing](#22-indexing)
- [23. Normalization](#23-normalization)
- [24. OLTP vs OLAP](#24-oltp-vs-olap)
- [25. Query Execution Order](#25-query-execution-order)
- [26. Query Optimization](#26-query-optimization)
- [27. 100 SQL Interview Questions](#27-100-sql-interview-questions)
- [28. Data Engineer Scenario Questions](#28-data-engineer-scenario-questions)
- [29. Final Revision Checklist](#29-final-revision-checklist)

---

# 1. SQL FUNDAMENTALS

## What is SQL?

SQL stands for **Structured Query Language**.

SQL is used to:

- Retrieve data
- Insert data
- Update data
- Delete data
- Create database objects
- Modify database objects
- Control transactions
- Query relational databases

### Example

```sql
SELECT *
FROM Employee;
```

---

## What is a Database?

A database is an organized collection of data that can be stored,
managed and retrieved efficiently.

---

## What is a Table?

A table stores data in:

- Rows
- Columns

Example:

| EmployeeID | Name | Salary |
|---|---|---:|
| 101 | Rahul | 50000 |
| 102 | Anil | 60000 |

---

# 2. SQL COMMAND TYPES

## DDL

Data Definition Language.

Used to define database structures.

```text
CREATE
ALTER
DROP
TRUNCATE
```

Example:

```sql
CREATE TABLE Employee
(
    EmployeeID INT,
    EmployeeName VARCHAR(100),
    Salary DECIMAL(10,2)
);
```

---

## DML

Data Manipulation Language.

```text
INSERT
UPDATE
DELETE
```

Example:

```sql
INSERT INTO Employee
VALUES (101, 'Rahul', 50000);
```

---

## DQL

Data Query Language.

```text
SELECT
```

---

## DCL

Data Control Language.

```text
GRANT
REVOKE
```

---

## TCL

Transaction Control Language.

```text
COMMIT
ROLLBACK
SAVEPOINT
```

---

# DELETE vs TRUNCATE vs DROP

| DELETE | TRUNCATE | DROP |
|---|---|---|
| Deletes rows | Removes all rows | Removes object |
| WHERE possible | WHERE not possible | WHERE not possible |
| Table remains | Table remains | Table removed |
| Usually slower | Usually faster | Removes structure |

### DELETE

```sql
DELETE FROM Employee
WHERE EmployeeID = 101;
```

### TRUNCATE

```sql
TRUNCATE TABLE Employee;
```

### DROP

```sql
DROP TABLE Employee;
```

---

# 3. KEYS AND CONSTRAINTS

# Primary Key

A Primary Key uniquely identifies every row.

Properties:

- Unique
- Cannot be NULL
- One primary-key constraint per table

```sql
CREATE TABLE Employee
(
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100)
);
```

---

# Foreign Key

A Foreign Key creates a relationship between tables.

```sql
CREATE TABLE Department
(
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
);
```

```sql
CREATE TABLE Employee
(
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    DepartmentID INT,

    FOREIGN KEY (DepartmentID)
    REFERENCES Department(DepartmentID)
);
```

---

# UNIQUE

Ensures uniqueness.

```sql
Email VARCHAR(100) UNIQUE
```

---

# NOT NULL

Prevents NULL.

```sql
EmployeeName VARCHAR(100) NOT NULL
```

---

# DEFAULT

Provides default value.

```sql
Status VARCHAR(20) DEFAULT 'ACTIVE'
```

---

# CHECK

Validates a condition.

```sql
Salary DECIMAL(10,2)
CHECK (Salary > 0)
```

---

# 4. JOINS

Joins are one of the most important SQL interview topics.

Types:

```text
INNER JOIN
LEFT JOIN
RIGHT JOIN
FULL OUTER JOIN
CROSS JOIN
SELF JOIN
```

---

# INNER JOIN

Returns matching records from both tables.

```sql
SELECT
    E.EmployeeName,
    D.DepartmentName
FROM Employee E
INNER JOIN Department D
    ON E.DepartmentID = D.DepartmentID;
```

### Interview Question

**What does INNER JOIN return?**

### Answer

It returns only rows where the join condition matches in both tables.

---

# LEFT JOIN

Returns:

- All rows from left table
- Matching rows from right table

```sql
SELECT
    E.EmployeeName,
    D.DepartmentName
FROM Employee E
LEFT JOIN Department D
    ON E.DepartmentID = D.DepartmentID;
```

---

# RIGHT JOIN

Returns all rows from the right table and matching rows from the left.

```sql
SELECT *
FROM Employee E
RIGHT JOIN Department D
    ON E.DepartmentID = D.DepartmentID;
```

---

# FULL OUTER JOIN

Returns:

- Matching rows
- Left-only rows
- Right-only rows

```sql
SELECT *
FROM Employee E
FULL OUTER JOIN Department D
    ON E.DepartmentID = D.DepartmentID;
```

---

# CROSS JOIN

Produces Cartesian product.

If:

```text
Employee = 5 rows
Department = 3 rows
```

Result:

```text
5 × 3 = 15 rows
```

```sql
SELECT *
FROM Employee
CROSS JOIN Department;
```

---

# SELF JOIN

A table joins with itself.

Example:

```text
EmployeeID
EmployeeName
ManagerID
```

Query:

```sql
SELECT
    E.EmployeeName AS Employee,
    M.EmployeeName AS Manager
FROM Employee E
LEFT JOIN Employee M
    ON E.ManagerID = M.EmployeeID;
```

---

# 5. AGGREGATIONS

Important aggregate functions:

```text
COUNT()
SUM()
AVG()
MIN()
MAX()
```

---

## COUNT

```sql
SELECT COUNT(*)
FROM Employee;
```

---

## SUM

```sql
SELECT SUM(Salary)
FROM Employee;
```

---

## AVG

```sql
SELECT AVG(Salary)
FROM Employee;
```

---

## MIN

```sql
SELECT MIN(Salary)
FROM Employee;
```

---

## MAX

```sql
SELECT MAX(Salary)
FROM Employee;
```

---

# GROUP BY

Groups rows.

```sql
SELECT
    DepartmentID,
    COUNT(*) AS EmployeeCount
FROM Employee
GROUP BY DepartmentID;
```

---

# HAVING

Filters groups.

```sql
SELECT
    DepartmentID,
    COUNT(*) AS EmployeeCount
FROM Employee
GROUP BY DepartmentID
HAVING COUNT(*) > 5;
```

---

# WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Filters rows | Filters groups |
| Before GROUP BY | After GROUP BY |
| Cannot normally use aggregate result directly | Used with aggregate conditions |

Example:

```sql
SELECT
    DepartmentID,
    COUNT(*) AS EmployeeCount
FROM Employee
WHERE Salary > 30000
GROUP BY DepartmentID
HAVING COUNT(*) > 5;
```

---

# 6. SUBQUERIES

A subquery is a query inside another query.

Example:

```sql
SELECT *
FROM Employee
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employee
);
```

---

# Types of Subqueries

```text
Scalar Subquery
Single-row Subquery
Multi-row Subquery
Correlated Subquery
Nested Subquery
```

---

# Second Highest Salary

```sql
SELECT MAX(Salary)
FROM Employee
WHERE Salary <
(
    SELECT MAX(Salary)
    FROM Employee
);
```

---

# Third Highest Salary

```sql
SELECT MAX(Salary)
FROM Employee
WHERE Salary <
(
    SELECT MAX(Salary)
    FROM Employee
    WHERE Salary <
    (
        SELECT MAX(Salary)
        FROM Employee
    )
);
```

---

# 7. CORRELATED SUBQUERIES

A correlated subquery references the outer query.

Example:

```sql
SELECT
    E.EmployeeName,
    E.Salary
FROM Employee E
WHERE E.Salary >
(
    SELECT AVG(E2.Salary)
    FROM Employee E2
    WHERE E2.DepartmentID = E.DepartmentID
);
```

Here:

```text
Outer query → E.DepartmentID
                    ↓
Inner query → E2.DepartmentID
```

The inner query depends on the outer row.

---

# Correlated vs Non-Correlated

## Non-correlated

```sql
SELECT *
FROM Employee
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employee
);
```

Inner query is independent.

## Correlated

```sql
SELECT *
FROM Employee E
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employee E2
    WHERE E2.DepartmentID = E.DepartmentID
);
```

Inner query depends on outer query.

---

# 8. CTE

CTE = Common Table Expression.

Syntax:

```sql
WITH CTE_Name AS
(
    SELECT ...
)
SELECT *
FROM CTE_Name;
```

---

## Example

```sql
WITH HighSalary AS
(
    SELECT *
    FROM Employee
    WHERE Salary > 50000
)
SELECT *
FROM HighSalary;
```

---

# Why use CTE?

CTEs improve:

- Readability
- Maintainability
- Debugging
- Complex query organization

They are also useful with:

- Window functions
- Recursive queries
- Multi-step transformations

---

# Multiple CTEs

```sql
WITH EmployeeData AS
(
    SELECT *
    FROM Employee
),

DepartmentData AS
(
    SELECT *
    FROM Department
)

SELECT *
FROM EmployeeData E
JOIN DepartmentData D
    ON E.DepartmentID = D.DepartmentID;
```

---

# CTE vs Subquery

| CTE | Subquery |
|---|---|
| Easier to read for complex logic | Good for small logic |
| Can define multiple CTEs | Nested structure can become harder to read |
| Supports recursive queries | Does not provide recursive CTE syntax |
| Named temporary query result | Inline query |

---

# 9. RECURSIVE CTE

Used for hierarchical data.

Example:

```text
CEO
 ├── Manager A
 │    ├── Employee 1
 │    └── Employee 2
 │
 └── Manager B
      └── Employee 3
```

Common use cases:

- Employee hierarchy
- Parent-child relationships
- Organization structures
- Category trees

Generic example:

```sql
WITH RECURSIVE EmployeeHierarchy AS
(
    SELECT
        EmployeeID,
        EmployeeName,
        ManagerID,
        1 AS Level
    FROM Employee
    WHERE ManagerID IS NULL

    UNION ALL

    SELECT
        E.EmployeeID,
        E.EmployeeName,
        E.ManagerID,
        H.Level + 1
    FROM Employee E
    JOIN EmployeeHierarchy H
        ON E.ManagerID = H.EmployeeID
)
SELECT *
FROM EmployeeHierarchy;
```

> Recursive CTE syntax varies by database.

---

# 10. WINDOW FUNCTIONS

Window functions are extremely important for Data Engineer interviews.

They perform calculations across related rows **without collapsing rows**.

Syntax:

```sql
FUNCTION()
OVER
(
    PARTITION BY ...
    ORDER BY ...
)
```

Important functions:

```text
ROW_NUMBER()
RANK()
DENSE_RANK()
LAG()
LEAD()
SUM() OVER()
AVG() OVER()
COUNT() OVER()
NTILE()
FIRST_VALUE()
LAST_VALUE()
```

---

# ROW_NUMBER

Assigns unique sequential numbers.

```sql
SELECT
    EmployeeName,
    Salary,
    ROW_NUMBER() OVER
    (
        ORDER BY Salary DESC
    ) AS rn
FROM Employee;
```

---

# RANK

Ties receive the same rank, with gaps.

```text
Salary     Rank

100000       1
90000        2
90000        2
80000        4
```

```sql
SELECT
    EmployeeName,
    Salary,
    RANK() OVER
    (
        ORDER BY Salary DESC
    ) AS SalaryRank
FROM Employee;
```

---

# DENSE_RANK

Ties receive same rank without gaps.

```text
100000 → 1
90000  → 2
90000  → 2
80000  → 3
```

---

# ROW_NUMBER vs RANK vs DENSE_RANK

| Function | Duplicate Rank | Gap |
|---|---|---|
| ROW_NUMBER | No | N/A |
| RANK | Yes | Yes |
| DENSE_RANK | Yes | No |

---

# PARTITION BY

Divides rows into groups for the window calculation.

Example:

```sql
SELECT
    EmployeeName,
    DepartmentID,
    Salary,

    RANK() OVER
    (
        PARTITION BY DepartmentID
        ORDER BY Salary DESC
    ) AS SalaryRank

FROM Employee;
```

This gives salary ranking **within each department**.

---

# Top 3 Employees Per Department

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY DepartmentID
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn <= 3;
```

---

# Highest Salary Per Department

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY DepartmentID
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

# Second Highest Salary

```sql
WITH Ranked AS
(
    SELECT
        Salary,
        DENSE_RANK() OVER
        (
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT Salary
FROM Ranked
WHERE rn = 2;
```

---

# LAG

Returns previous row value.

```sql
SELECT
    EmployeeID,
    Salary,
    LAG(Salary) OVER
    (
        ORDER BY EmployeeID
    ) AS PreviousSalary
FROM Employee;
```

---

# LEAD

Returns next row value.

```sql
SELECT
    EmployeeID,
    Salary,
    LEAD(Salary) OVER
    (
        ORDER BY EmployeeID
    ) AS NextSalary
FROM Employee;
```

---

# Running Total

```sql
SELECT
    OrderDate,
    Amount,

    SUM(Amount) OVER
    (
        ORDER BY OrderDate
    ) AS RunningTotal

FROM Orders;
```

---

# Running Total Per Customer

```sql
SELECT
    CustomerID,
    OrderDate,
    Amount,

    SUM(Amount) OVER
    (
        PARTITION BY CustomerID
        ORDER BY OrderDate
    ) AS RunningTotal

FROM Orders;
```

---

# 11. NULL HANDLING

NULL means:

```text
Unknown / missing / unavailable value
```

NULL is NOT:

```text
0
''
'NULL'
```

---

# IS NULL

Wrong:

```sql
WHERE ManagerID = NULL
```

Correct:

```sql
WHERE ManagerID IS NULL;
```

---

# IS NOT NULL

```sql
SELECT *
FROM Employee
WHERE ManagerID IS NOT NULL;
```

---

# COALESCE

Returns the first non-NULL value.

```sql
SELECT
    COALESCE(Phone, 'Not Available')
FROM Employee;
```

---

# NULLIF

Returns NULL when two expressions are equal.

Useful for divide-by-zero:

```sql
SELECT
    Revenue / NULLIF(Quantity, 0)
FROM Sales;
```

---

# 12. CASE

Used for conditional logic.

```sql
SELECT
    EmployeeName,
    Salary,

    CASE
        WHEN Salary >= 100000 THEN 'HIGH'
        WHEN Salary >= 50000 THEN 'MEDIUM'
        ELSE 'LOW'
    END AS SalaryCategory

FROM Employee;
```

---

# 13. SET OPERATORS

Important:

```text
UNION
UNION ALL
INTERSECT
EXCEPT
```

---

# UNION

Removes duplicates.

```sql
SELECT EmployeeID
FROM Employee2025

UNION

SELECT EmployeeID
FROM Employee2026;
```

---

# UNION ALL

Keeps duplicates.

```sql
SELECT EmployeeID
FROM Employee2025

UNION ALL

SELECT EmployeeID
FROM Employee2026;
```

### Interview Question

**Which is faster: UNION or UNION ALL?**

### Answer

Generally `UNION ALL`, because it does not need to perform duplicate elimination.

---

# INTERSECT

Returns common rows.

```sql
SELECT EmployeeID
FROM Employee2025

INTERSECT

SELECT EmployeeID
FROM Employee2026;
```

---

# EXCEPT

Returns rows in first query but not second.

```sql
SELECT EmployeeID
FROM Employee2025

EXCEPT

SELECT EmployeeID
FROM Employee2026;
```

---

# 14. DATE AND STRING FUNCTIONS

## Names starting with A

```sql
SELECT *
FROM Employee
WHERE EmployeeName LIKE 'A%';
```

---

## Names ending with N

```sql
SELECT *
FROM Employee
WHERE EmployeeName LIKE '%n';
```

---

## Names containing AN

```sql
SELECT *
FROM Employee
WHERE EmployeeName LIKE '%an%';
```

---

# Date Filtering

Instead of:

```sql
WHERE YEAR(OrderDate) = 2026
```

Prefer:

```sql
WHERE OrderDate >= '2026-01-01'
AND OrderDate < '2027-01-01';
```

This can be more index-friendly.

---

# 15. DUPLICATE HANDLING

## Find duplicates

```sql
SELECT
    EmployeeName,
    DepartmentID,
    COUNT(*) AS DuplicateCount
FROM Employee
GROUP BY
    EmployeeName,
    DepartmentID
HAVING COUNT(*) > 1;
```

---

# Find Duplicate Rows Using ROW_NUMBER

```sql
SELECT *
FROM
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY EmployeeName, DepartmentID
            ORDER BY EmployeeID
        ) AS rn
    FROM Employee
) X
WHERE rn > 1;
```

---

# Latest Record Per Business Key

This is one of the **most important Data Engineer SQL patterns**.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY CustomerID
            ORDER BY UpdatedDate DESC
        ) AS rn
    FROM Customer
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

Used in:

```text
Deduplication
CDC
Incremental loads
SCD
Data pipelines
Latest-record logic
```

---

# 16. TRANSACTIONS

A transaction is a logical unit of work.

Example:

```text
Transfer ₹10,000

Account A
    ↓
Debit ₹10,000

Account B
    ↓
Credit ₹10,000
```

Both should succeed or both should fail.

---

# BEGIN TRANSACTION

Generic syntax:

```sql
BEGIN TRANSACTION;
```

---

# COMMIT

Makes changes permanent.

```sql
COMMIT;
```

---

# ROLLBACK

Undo uncommitted changes.

```sql
ROLLBACK;
```

---

# SAVEPOINT

Allows partial rollback.

```sql
SAVEPOINT sp1;

ROLLBACK TO sp1;
```

> Exact syntax differs by database.

---

# 17. ACID PROPERTIES

ACID:

```text
A → Atomicity
C → Consistency
I → Isolation
D → Durability
```

---

# Atomicity

All operations succeed or none succeed.

```text
Debit
+
Credit

Both succeed
OR
Both rollback
```

---

# Consistency

The transaction must move the database from one valid state to another valid state.

Constraints and business rules should remain valid.

---

# Isolation

Concurrent transactions should not incorrectly interfere with each other.

---

# Durability

Once a transaction is committed, its changes should survive failures.

---

# Interview Question

## Explain ACID with a bank transaction.

### Answer

Suppose ₹10,000 is transferred from Account A to Account B.

- **Atomicity:** Debit and credit happen together.
- **Consistency:** Account balances remain valid.
- **Isolation:** Other transactions should not see an inconsistent intermediate state.
- **Durability:** After COMMIT, the transfer remains even after a system crash.

---

# 18. CONCURRENCY

Concurrency means multiple transactions operate at the same time.

Example:

```text
Transaction A
       ↓
Reads Salary

Transaction B
       ↓
Updates Salary
```

Concurrency can create problems.

---

# Dirty Read

Transaction A reads uncommitted data from Transaction B.

```text
B → UPDATE
A → READ
B → ROLLBACK
```

A read data that never became permanent.

---

# Non-Repeatable Read

Same row is read twice and produces different values.

```text
A → READ salary = 50000

B → UPDATE salary = 60000
B → COMMIT

A → READ salary = 60000
```

---

# Phantom Read

Same query returns a different set of rows because another transaction inserted/deleted rows.

Example:

```text
First query → 10 employees

Another transaction inserts employee

Second query → 11 employees
```

---

# Lost Update

Two transactions update the same data and one update overwrites the other.

---

# 19. ISOLATION LEVELS

Common isolation levels:

```text
READ UNCOMMITTED
READ COMMITTED
REPEATABLE READ
SERIALIZABLE
```

Some databases also support:

```text
SNAPSHOT
```

---

# READ UNCOMMITTED

Lowest isolation.

Can allow:

```text
Dirty Reads
Non-repeatable Reads
Phantom Reads
```

---

# READ COMMITTED

Prevents dirty reads.

But non-repeatable and phantom reads can still occur.

---

# REPEATABLE READ

Prevents:

```text
Dirty reads
Non-repeatable reads
```

Phantom behavior depends on the database.

---

# SERIALIZABLE

Highest traditional isolation level.

Provides strongest consistency but can reduce concurrency.

---

# Isolation Table

| Isolation | Dirty Read | Non-repeatable Read | Phantom |
|---|---|---|---|
| Read Uncommitted | Possible | Possible | Possible |
| Read Committed | No | Possible | Possible |
| Repeatable Read | No | No | DB-dependent |
| Serializable | No | No | No |

---

# 20. LOCKS

Locks control concurrent access.

Important types:

```text
Shared Lock
Exclusive Lock
```

---

# Shared Lock

Used for reading.

Multiple transactions may generally hold compatible shared locks.

---

# Exclusive Lock

Used for modifications.

```text
INSERT
UPDATE
DELETE
```

---

# 21. DEADLOCK

Deadlock occurs when transactions wait for each other.

Example:

```text
Transaction A
    ↓
Locks Table A
    ↓
Waits for Table B


Transaction B
    ↓
Locks Table B
    ↓
Waits for Table A
```

Result:

```text
A waits for B
B waits for A
```

Database detects the deadlock and normally aborts one transaction.

---

# How to Reduce Deadlocks

```text
1. Keep transactions short
2. Access objects in consistent order
3. Avoid unnecessary locks
4. Use appropriate indexes
5. Commit quickly
6. Avoid long user interaction inside transactions
```

---

# 22. INDEXING

An index improves data retrieval.

Think of it like the index of a book.

Without index:

```text
Search many/all rows
```

With index:

```text
Index
 ↓
Locate matching rows
 ↓
Access required data
```

---

# Clustered Index

In database systems that support clustered storage, a clustered index organizes table data according to the index key.

Typically:

```text
One clustered index per table
```

---

# Non-Clustered Index

Separate index structure that points to table data.

A table can generally have multiple non-clustered indexes.

---

# Composite Index

Index on multiple columns.

```sql
CREATE INDEX idx_employee
ON Employee(DepartmentID, Salary);
```

Column order matters.

---

# Covering Index

An index containing all columns required by a query.

Example:

```sql
SELECT
    EmployeeName,
    Salary
FROM Employee
WHERE DepartmentID = 10;
```

A suitable covering index may include:

```text
DepartmentID
EmployeeName
Salary
```

---

# When Should We Use Indexes?

Good candidates:

```text
WHERE columns
JOIN columns
ORDER BY columns
GROUP BY columns
Frequently searched columns
```

---

# Disadvantages of Too Many Indexes

Indexes can:

```text
Consume storage
Slow INSERT
Slow UPDATE
Slow DELETE
Increase maintenance
```

---

# Composite Index and Column Order

Suppose:

```sql
CREATE INDEX idx_employee
ON Employee(DepartmentID, Salary, EmployeeName);
```

The leading column:

```text
DepartmentID
```

is important for efficient index use.

A query filtering only on:

```text
Salary
```

may not benefit as much.

---

# SARGABLE QUERY

SARG = Search ARGument Able.

Bad:

```sql
WHERE YEAR(OrderDate) = 2026;
```

Better:

```sql
WHERE OrderDate >= '2026-01-01'
AND OrderDate < '2027-01-01';
```

---

# 23. NORMALIZATION

Normalization reduces unnecessary data duplication.

---

# 1NF

First Normal Form:

```text
Atomic values
No repeating groups
```

Bad:

```text
EmployeeID | Skills
101        | SQL, Python, Spark
```

Better:

```text
EmployeeID | Skill
101        | SQL
101        | Python
101        | Spark
```

---

# 2NF

Requirements:

```text
1NF
+
No partial dependency on part of a composite key
```

---

# 3NF

Requirements:

```text
2NF
+
No transitive dependency
```

Example:

```text
EmployeeID
DepartmentID
DepartmentName
```

If:

```text
EmployeeID → DepartmentID
DepartmentID → DepartmentName
```

DepartmentName should generally belong to Department table.

---

# Denormalization

Intentionally adding redundancy for performance/read efficiency.

Common in:

```text
Data Warehouses
Reporting Systems
Analytics Systems
```

---

# 24. OLTP vs OLAP

| OLTP | OLAP |
|---|---|
| Transaction processing | Analytics |
| Many INSERT/UPDATE operations | Mostly reads |
| Highly normalized | Often denormalized |
| Short transactions | Complex analytical queries |
| Current operational data | Historical/analytical data |

---

# 25. QUERY EXECUTION ORDER

Very important interview topic.

We write:

```sql
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
```

But logical processing is approximately:

```text
1. FROM
2. JOIN
3. WHERE
4. GROUP BY
5. HAVING
6. SELECT
7. DISTINCT
8. ORDER BY
9. LIMIT / TOP
```

This is why a SELECT alias generally cannot be used directly in WHERE.

---

# 26. QUERY OPTIMIZATION

When a query is slow, check:

```text
1. Execution plan
2. Indexes
3. Table scans
4. Join conditions
5. Join cardinality
6. Functions on indexed columns
7. SELECT *
8. DISTINCT
9. ORDER BY
10. Statistics
11. Data volume
12. Partitioning
```

---

# Avoid SELECT *

Instead of:

```sql
SELECT *
FROM Employee;
```

Prefer:

```sql
SELECT
    EmployeeID,
    EmployeeName,
    Salary
FROM Employee;
```

Benefits:

- Less data transferred
- Better readability
- Potentially better performance

---

# 27. 100 SQL INTERVIEW QUESTIONS

# BASIC

## Q1. What is SQL?

### Answer

SQL is Structured Query Language used to interact with relational databases.

---

## Q2. What is a primary key?

### Answer

A key that uniquely identifies each row and does not allow NULL values.

---

## Q3. What is a foreign key?

### Answer

A column or set of columns that references a key in another table.

---

## Q4. DELETE vs TRUNCATE?

### Answer

`DELETE` can remove selected rows using WHERE.

`TRUNCATE` removes all rows and normally cannot use WHERE.

---

## Q5. What is DISTINCT?

### Answer

It removes duplicate result rows.

```sql
SELECT DISTINCT DepartmentID
FROM Employee;
```

---

## Q6. What is GROUP BY?

### Answer

Groups rows so aggregate functions can be applied.

---

## Q7. What is HAVING?

### Answer

Filters grouped/aggregated results.

---

## Q8. WHERE vs HAVING?

### Answer

```text
WHERE  → rows
HAVING → groups
```

---

## Q9. What are aggregate functions?

### Answer

```text
COUNT
SUM
AVG
MIN
MAX
```

---

## Q10. What is NULL?

### Answer

NULL represents an unknown, missing, or unavailable value.

---

# JOINS

## Q11. What is INNER JOIN?

Returns matching rows from both tables.

---

## Q12. What is LEFT JOIN?

Returns all left rows and matching right rows.

---

## Q13. What is RIGHT JOIN?

Returns all right rows and matching left rows.

---

## Q14. What is FULL OUTER JOIN?

Returns matched and unmatched rows from both tables.

---

## Q15. What is CROSS JOIN?

Returns Cartesian product.

---

## Q16. What is SELF JOIN?

Joining a table to itself.

---

## Q17. Find employees with department names.

```sql
SELECT
    E.EmployeeName,
    D.DepartmentName
FROM Employee E
JOIN Department D
    ON E.DepartmentID = D.DepartmentID;
```

---

## Q18. Find employees without departments.

```sql
SELECT E.*
FROM Employee E
LEFT JOIN Department D
    ON E.DepartmentID = D.DepartmentID
WHERE D.DepartmentID IS NULL;
```

---

## Q19. Find departments without employees.

```sql
SELECT D.*
FROM Department D
LEFT JOIN Employee E
    ON D.DepartmentID = E.DepartmentID
WHERE E.EmployeeID IS NULL;
```

---

## Q20. Find employee and manager names.

```sql
SELECT
    E.EmployeeName AS Employee,
    M.EmployeeName AS Manager
FROM Employee E
LEFT JOIN Employee M
    ON E.ManagerID = M.EmployeeID;
```

---

# AGGREGATION

## Q21. Department-wise employee count.

```sql
SELECT
    DepartmentID,
    COUNT(*) AS EmployeeCount
FROM Employee
GROUP BY DepartmentID;
```

---

## Q22. Department-wise average salary.

```sql
SELECT
    DepartmentID,
    AVG(Salary) AS AvgSalary
FROM Employee
GROUP BY DepartmentID;
```

---

## Q23. Departments having more than 5 employees.

```sql
SELECT
    DepartmentID,
    COUNT(*) AS EmployeeCount
FROM Employee
GROUP BY DepartmentID
HAVING COUNT(*) > 5;
```

---

## Q24. Highest salary.

```sql
SELECT MAX(Salary)
FROM Employee;
```

---

## Q25. Lowest salary.

```sql
SELECT MIN(Salary)
FROM Employee;
```

---

# SUBQUERIES

## Q26. Employees earning above average salary.

```sql
SELECT *
FROM Employee
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employee
);
```

---

## Q27. Employees with maximum salary.

```sql
SELECT *
FROM Employee
WHERE Salary =
(
    SELECT MAX(Salary)
    FROM Employee
);
```

---

## Q28. Second-highest salary.

```sql
SELECT MAX(Salary)
FROM Employee
WHERE Salary <
(
    SELECT MAX(Salary)
    FROM Employee
);
```

---

## Q29. Third-highest salary.

```sql
WITH Ranked AS
(
    SELECT
        Salary,
        DENSE_RANK() OVER
        (
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT Salary
FROM Ranked
WHERE rn = 3;
```

---

## Q30. Employees above department average.

```sql
SELECT E.*
FROM Employee E
WHERE E.Salary >
(
    SELECT AVG(E2.Salary)
    FROM Employee E2
    WHERE E2.DepartmentID = E.DepartmentID
);
```

---

# CORRELATED SUBQUERIES

## Q31. What is correlated subquery?

### Answer

A subquery that references a column from the outer query.

---

## Q32. Find employees above department average.

```sql
SELECT E.*
FROM Employee E
WHERE E.Salary >
(
    SELECT AVG(E2.Salary)
    FROM Employee E2
    WHERE E2.DepartmentID = E.DepartmentID
);
```

---

## Q33. Find departments having employee earning above 100000.

```sql
SELECT D.*
FROM Department D
WHERE EXISTS
(
    SELECT 1
    FROM Employee E
    WHERE E.DepartmentID = D.DepartmentID
      AND E.Salary > 100000
);
```

---

# CTE

## Q34. What is CTE?

### Answer

A CTE is a named temporary query result defined using `WITH` for the duration of a statement.

---

## Q35. Employees above average using CTE.

```sql
WITH AvgSalary AS
(
    SELECT AVG(Salary) AS AvgSal
    FROM Employee
)
SELECT E.*
FROM Employee E
CROSS JOIN AvgSalary A
WHERE E.Salary > A.AvgSal;
```

---

## Q36. Department average using CTE.

```sql
WITH DeptAvg AS
(
    SELECT
        DepartmentID,
        AVG(Salary) AS AvgSalary
    FROM Employee
    GROUP BY DepartmentID
)
SELECT *
FROM DeptAvg;
```

---

## Q37. Can multiple CTEs be used?

Yes.

```sql
WITH E AS
(
    SELECT *
    FROM Employee
),
D AS
(
    SELECT *
    FROM Department
)
SELECT *
FROM E
JOIN D
    ON E.DepartmentID = D.DepartmentID;
```

---

## Q38. What is recursive CTE?

A CTE that references itself, commonly used for hierarchical data.

---

# WINDOW FUNCTIONS

## Q39. What is a window function?

A function that calculates values across related rows without grouping them into one output row.

---

## Q40. Rank employees by salary.

```sql
SELECT
    EmployeeName,
    Salary,
    RANK() OVER
    (
        ORDER BY Salary DESC
    ) AS SalaryRank
FROM Employee;
```

---

## Q41. Department-wise salary rank.

```sql
SELECT
    EmployeeName,
    DepartmentID,
    Salary,
    RANK() OVER
    (
        PARTITION BY DepartmentID
        ORDER BY Salary DESC
    ) AS SalaryRank
FROM Employee;
```

---

## Q42. Second-highest salary using DENSE_RANK.

```sql
WITH Ranked AS
(
    SELECT
        Salary,
        DENSE_RANK() OVER
        (
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT Salary
FROM Ranked
WHERE rn = 2;
```

---

## Q43. Top 3 employees per department.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY DepartmentID
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn <= 3;
```

---

## Q44. ROW_NUMBER vs RANK?

### Answer

`ROW_NUMBER()` gives unique numbers.

`RANK()` gives same rank to ties and leaves gaps.

---

## Q45. RANK vs DENSE_RANK?

### Answer

```text
RANK:

1
2
2
4

DENSE_RANK:

1
2
2
3
```

---

## Q46. Previous salary.

```sql
SELECT
    EmployeeID,
    Salary,
    LAG(Salary) OVER
    (
        ORDER BY EmployeeID
    ) AS PreviousSalary
FROM Employee;
```

---

## Q47. Next salary.

```sql
SELECT
    EmployeeID,
    Salary,
    LEAD(Salary) OVER
    (
        ORDER BY EmployeeID
    ) AS NextSalary
FROM Employee;
```

---

## Q48. Salary difference from previous row.

```sql
SELECT
    EmployeeID,
    Salary,
    Salary -
    LAG(Salary) OVER
    (
        ORDER BY EmployeeID
    ) AS Difference
FROM Employee;
```

---

## Q49. Running total.

```sql
SELECT
    EmployeeID,
    Salary,
    SUM(Salary) OVER
    (
        ORDER BY EmployeeID
    ) AS RunningTotal
FROM Employee;
```

---

## Q50. Highest-paid employee per department.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY DepartmentID
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

# DUPLICATES

## Q51. Find duplicate employee names.

```sql
SELECT
    EmployeeName,
    COUNT(*) AS cnt
FROM Employee
GROUP BY EmployeeName
HAVING COUNT(*) > 1;
```

---

## Q52. Find duplicate records using ROW_NUMBER.

```sql
SELECT *
FROM
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY EmployeeName, DepartmentID
            ORDER BY EmployeeID
        ) AS rn
    FROM Employee
) X
WHERE rn > 1;
```

---

## Q53. Find records to keep from duplicates.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY EmployeeName, DepartmentID
            ORDER BY EmployeeID
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

# NULL

## Q54. Employees with NULL manager.

```sql
SELECT *
FROM Employee
WHERE ManagerID IS NULL;
```

---

## Q55. Replace NULL salary with 0.

```sql
SELECT
    COALESCE(Salary, 0)
FROM Employee;
```

---

## Q56. Why doesn't `Salary = NULL` work?

### Answer

NULL represents an unknown value and comparisons using `=` do not evaluate it as TRUE.

Use:

```sql
IS NULL
```

---

# CASE

## Q57. Salary classification.

```sql
SELECT
    EmployeeName,
    Salary,

    CASE
        WHEN Salary >= 100000 THEN 'HIGH'
        WHEN Salary >= 50000 THEN 'MEDIUM'
        ELSE 'LOW'
    END AS Category

FROM Employee;
```

---

## Q58. Count employees by salary category.

```sql
SELECT
    CASE
        WHEN Salary >= 100000 THEN 'HIGH'
        WHEN Salary >= 50000 THEN 'MEDIUM'
        ELSE 'LOW'
    END AS Category,

    COUNT(*) AS EmployeeCount

FROM Employee

GROUP BY
    CASE
        WHEN Salary >= 100000 THEN 'HIGH'
        WHEN Salary >= 50000 THEN 'MEDIUM'
        ELSE 'LOW'
    END;
```

---

# EXISTS / IN

## Q59. Find employees with valid departments.

```sql
SELECT *
FROM Employee E
WHERE EXISTS
(
    SELECT 1
    FROM Department D
    WHERE D.DepartmentID = E.DepartmentID
);
```

---

## Q60. EXISTS vs IN?

### Answer

`IN` compares a value against a set.

`EXISTS` checks whether at least one matching row exists.

For correlated existence checks, `EXISTS` is often a natural choice.

---

# ADVANCED

## Q61. Top 2 salaries per department.

```sql
WITH Ranked AS
(
    SELECT
        *,
        DENSE_RANK() OVER
        (
            PARTITION BY DepartmentID
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn <= 2;
```

---

## Q62. Employees above department average.

```sql
WITH DeptAvg AS
(
    SELECT
        DepartmentID,
        AVG(Salary) AS AvgSalary
    FROM Employee
    GROUP BY DepartmentID
)
SELECT E.*
FROM Employee E
JOIN DeptAvg D
    ON E.DepartmentID = D.DepartmentID
WHERE E.Salary > D.AvgSalary;
```

---

## Q63. Employees with duplicate salary.

```sql
SELECT *
FROM Employee
WHERE Salary IN
(
    SELECT Salary
    FROM Employee
    GROUP BY Salary
    HAVING COUNT(*) > 1
);
```

---

## Q64. Departments where average salary > company average.

```sql
WITH DeptAvg AS
(
    SELECT
        DepartmentID,
        AVG(Salary) AS DeptAvgSalary
    FROM Employee
    GROUP BY DepartmentID
)
SELECT *
FROM DeptAvg
WHERE DeptAvgSalary >
(
    SELECT AVG(Salary)
    FROM Employee
);
```

---

## Q65. First employee in every department.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY DepartmentID
            ORDER BY JoinDate
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

## Q66. Latest employee in every department.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY DepartmentID
            ORDER BY JoinDate DESC
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

## Q67. Employees who joined after their manager.

```sql
SELECT
    E.EmployeeName,
    E.JoinDate,
    M.EmployeeName AS ManagerName,
    M.JoinDate AS ManagerJoinDate
FROM Employee E
JOIN Employee M
    ON E.ManagerID = M.EmployeeID
WHERE E.JoinDate > M.JoinDate;
```

---

## Q68. Customers without orders.

```sql
SELECT C.*
FROM Customer C
LEFT JOIN Orders O
    ON C.CustomerID = O.CustomerID
WHERE O.CustomerID IS NULL;
```

---

## Q69. Customers with more than 3 orders.

```sql
SELECT
    CustomerID,
    COUNT(*) AS OrderCount
FROM Orders
GROUP BY CustomerID
HAVING COUNT(*) > 3;
```

---

## Q70. Latest order per customer.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY CustomerID
            ORDER BY OrderDate DESC
        ) AS rn
    FROM Orders
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

## Q71. Running total per customer.

```sql
SELECT
    CustomerID,
    OrderDate,
    Amount,

    SUM(Amount) OVER
    (
        PARTITION BY CustomerID
        ORDER BY OrderDate
    ) AS RunningTotal

FROM Orders;
```

---

## Q72. Month-over-month sales.

```sql
WITH Monthly AS
(
    SELECT
        SaleMonth,
        SUM(Amount) AS Sales
    FROM Sales
    GROUP BY SaleMonth
),
Comparison AS
(
    SELECT
        *,
        LAG(Sales) OVER
        (
            ORDER BY SaleMonth
        ) AS PreviousSales
    FROM Monthly
)
SELECT
    SaleMonth,
    Sales,
    PreviousSales,
    Sales - PreviousSales AS Difference
FROM Comparison;
```

---

## Q73. Find percentage contribution by department.

```sql
SELECT
    DepartmentID,
    SUM(Salary) AS DepartmentSalary,

    SUM(Salary) * 100.0 /
    SUM(SUM(Salary)) OVER () AS Percentage

FROM Employee

GROUP BY DepartmentID;
```

---

## Q74. Departments where every employee earns > 50000.

```sql
SELECT DepartmentID
FROM Employee
GROUP BY DepartmentID
HAVING MIN(Salary) > 50000;
```

---

## Q75. Departments where at least one employee earns > 100000.

```sql
SELECT DepartmentID
FROM Employee
GROUP BY DepartmentID
HAVING MAX(Salary) > 100000;
```

---

## Q76. Difference between highest and lowest salary.

```sql
SELECT
    MAX(Salary) - MIN(Salary) AS SalaryDifference
FROM Employee;
```

---

## Q77. Departments with salary difference > 50000.

```sql
SELECT
    DepartmentID,
    MAX(Salary) - MIN(Salary) AS SalaryDifference
FROM Employee
GROUP BY DepartmentID
HAVING MAX(Salary) - MIN(Salary) > 50000;
```

---

## Q78. Latest record per business key.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY BusinessKey
            ORDER BY UpdatedDate DESC
        ) AS rn
    FROM SourceTable
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

## Q79. Source records missing in target.

```sql
SELECT S.*
FROM SourceTable S
LEFT JOIN TargetTable T
    ON S.BusinessKey = T.BusinessKey
WHERE T.BusinessKey IS NULL;
```

---

## Q80. Target records missing in source.

```sql
SELECT T.*
FROM TargetTable T
LEFT JOIN SourceTable S
    ON T.BusinessKey = S.BusinessKey
WHERE S.BusinessKey IS NULL;
```

---

## Q81. Source-target value mismatch.

```sql
SELECT
    S.BusinessKey,
    S.Amount AS SourceAmount,
    T.Amount AS TargetAmount
FROM SourceTable S
JOIN TargetTable T
    ON S.BusinessKey = T.BusinessKey
WHERE
    COALESCE(S.Amount, 0)
    <>
    COALESCE(T.Amount, 0);
```

---

## Q82. Find changed records.

```sql
SELECT S.*
FROM SourceTable S
JOIN TargetTable T
    ON S.BusinessKey = T.BusinessKey
WHERE
       COALESCE(S.Name, '') <> COALESCE(T.Name, '')
    OR COALESCE(S.Salary, 0) <> COALESCE(T.Salary, 0);
```

---

## Q83. Find new records.

```sql
SELECT S.*
FROM SourceTable S
LEFT JOIN TargetTable T
    ON S.BusinessKey = T.BusinessKey
WHERE T.BusinessKey IS NULL;
```

---

## Q84. Find employees whose salary increased.

```sql
WITH SalaryData AS
(
    SELECT
        EmployeeID,
        EffectiveDate,
        Salary,

        LAG(Salary) OVER
        (
            PARTITION BY EmployeeID
            ORDER BY EffectiveDate
        ) AS PreviousSalary

    FROM SalaryHistory
)
SELECT *
FROM SalaryData
WHERE Salary > PreviousSalary;
```

---

## Q85. Find highest transaction per customer.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY CustomerID
            ORDER BY Amount DESC
        ) AS rn
    FROM Transactions
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

## Q86. Find customers whose monthly sales increased.

```sql
WITH Monthly AS
(
    SELECT
        CustomerID,
        SaleMonth,
        SUM(Amount) AS Sales
    FROM Sales
    GROUP BY CustomerID, SaleMonth
),
Comparison AS
(
    SELECT
        *,
        LAG(Sales) OVER
        (
            PARTITION BY CustomerID
            ORDER BY SaleMonth
        ) AS PreviousSales
    FROM Monthly
)
SELECT *
FROM Comparison
WHERE Sales > PreviousSales;
```

---

## Q87. Find missing dates.

```sql
SELECT C.CalendarDate
FROM Calendar C
LEFT JOIN Sales S
    ON C.CalendarDate = S.SaleDate
WHERE S.SaleDate IS NULL;
```

---

## Q88. Find employees without activity.

```sql
SELECT E.*
FROM Employee E
LEFT JOIN EmployeeActivity A
    ON E.EmployeeID = A.EmployeeID
WHERE A.EmployeeID IS NULL;
```

---

## Q89. Find records existing in source but not target.

```sql
SELECT S.*
FROM Source S
WHERE NOT EXISTS
(
    SELECT 1
    FROM Target T
    WHERE T.BusinessKey = S.BusinessKey
);
```

---

## Q90. Find records common to source and target.

```sql
SELECT S.BusinessKey
FROM Source S
JOIN Target T
    ON S.BusinessKey = T.BusinessKey;
```

---

## Q91. Find salary difference between employee and manager.

```sql
SELECT
    E.EmployeeName,
    E.Salary AS EmployeeSalary,
    M.EmployeeName AS Manager,
    M.Salary AS ManagerSalary,
    E.Salary - M.Salary AS Difference
FROM Employee E
JOIN Employee M
    ON E.ManagerID = M.EmployeeID;
```

---

## Q92. Find employees earning more than their manager.

```sql
SELECT E.*
FROM Employee E
JOIN Employee M
    ON E.ManagerID = M.EmployeeID
WHERE E.Salary > M.Salary;
```

---

## Q93. Find departments with no employees.

```sql
SELECT D.*
FROM Department D
LEFT JOIN Employee E
    ON D.DepartmentID = E.DepartmentID
WHERE E.EmployeeID IS NULL;
```

---

## Q94. Find employees with same salary and department.

```sql
SELECT
    DepartmentID,
    Salary,
    COUNT(*) AS EmployeeCount
FROM Employee
GROUP BY
    DepartmentID,
    Salary
HAVING COUNT(*) > 1;
```

---

## Q95. Find maximum salary in each department.

```sql
SELECT
    DepartmentID,
    MAX(Salary) AS MaxSalary
FROM Employee
GROUP BY DepartmentID;
```

---

## Q96. Find minimum salary in each department.

```sql
SELECT
    DepartmentID,
    MIN(Salary) AS MinSalary
FROM Employee
GROUP BY DepartmentID;
```

---

## Q97. Find total salary by department.

```sql
SELECT
    DepartmentID,
    SUM(Salary) AS TotalSalary
FROM Employee
GROUP BY DepartmentID;
```

---

## Q98. Find average salary by department.

```sql
SELECT
    DepartmentID,
    AVG(Salary) AS AverageSalary
FROM Employee
GROUP BY DepartmentID;
```

---

## Q99. Find latest record for every employee.

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY EmployeeID
            ORDER BY UpdatedDate DESC
        ) AS rn
    FROM EmployeeHistory
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

## Q100. Find top 3 salaries overall.

```sql
WITH Ranked AS
(
    SELECT
        Salary,
        DENSE_RANK() OVER
        (
            ORDER BY Salary DESC
        ) AS rn
    FROM Employee
)
SELECT DISTINCT Salary
FROM Ranked
WHERE rn <= 3;
```

---

# 28. DATA ENGINEER SCENARIO-BASED QUESTIONS

This section is especially important for:

```text
Azure Data Engineer
Data Engineer
ETL Developer
Data Platform Engineer
Databricks Engineer
```

---

# Scenario 1: Duplicate Data Loaded

### Interviewer

Your ADF pipeline loaded duplicate records into the target table.

How will you identify them?

### Answer

First identify the business key.

```sql
SELECT
    BusinessKey,
    COUNT(*) AS cnt
FROM Target
GROUP BY BusinessKey
HAVING COUNT(*) > 1;
```

Then use:

```sql
ROW_NUMBER()
```

to identify which record should be retained.

---

# Scenario 2: Latest Record

### Interviewer

Customer data arrives multiple times. How do you select the latest record?

### Answer

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY CustomerID
            ORDER BY UpdatedDate DESC
        ) AS rn
    FROM Customer
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

# Scenario 3: Source Has 10,000 Rows and Target Has 9,950

### Interviewer

How do you identify the missing 50 records?

### Answer

```sql
SELECT S.*
FROM Source S
LEFT JOIN Target T
    ON S.BusinessKey = T.BusinessKey
WHERE T.BusinessKey IS NULL;
```

---

# Scenario 4: Source and Target Counts Match but Data Differs

### Answer

Count validation alone is not sufficient.

I would perform:

```text
1. Business-key reconciliation
2. Column-level comparison
3. Aggregate comparison
4. NULL comparison
5. Duplicate check
```

Example:

```sql
SELECT
    S.BusinessKey,
    S.Amount AS SourceAmount,
    T.Amount AS TargetAmount
FROM Source S
JOIN Target T
    ON S.BusinessKey = T.BusinessKey
WHERE
    COALESCE(S.Amount, 0)
    <>
    COALESCE(T.Amount, 0);
```

---

# Scenario 5: ADF Pipeline Successfully Completed

### Interviewer

How do you validate that the pipeline loaded correct data?

### Answer

I would validate:

```text
Source row count
Target row count
Duplicate records
NULL records
Business keys
Source-target reconciliation
Aggregates
Load timestamp
Incremental watermark
```

---

# Scenario 6: Incremental Load

### Interviewer

How do you load only newly modified records?

### Answer

Use a watermark column such as:

```text
ModifiedDate
LastUpdatedTimestamp
Identity column
CDC position
```

Example:

```sql
SELECT *
FROM Source
WHERE ModifiedDate > '2026-10-10 23:00:00';
```

---

# Scenario 7: Late Arriving Data

### Interviewer

What if a record arrives late?

### Answer

I would use a strategy such as:

```text
Lookback window
Watermark adjustment
CDC
Reprocessing
Upsert/MERGE logic
```

Example:

```text
Last successful watermark
        ↓
Look back 1–2 days
        ↓
Reload affected records
        ↓
Deduplicate
        ↓
Merge into target
```

---

# Scenario 8: Query Is Slow

### Interviewer

A query takes 20 minutes. What will you do?

### Answer

I would investigate:

```text
1. Execution plan
2. Full table scans
3. Missing indexes
4. Join conditions
5. Join cardinality
6. Filtering
7. Functions on indexed columns
8. SELECT *
9. DISTINCT
10. Statistics
11. Partition pruning
12. Data volume
```

I would not immediately create an index without checking the execution plan.

---

# Scenario 9: Query Returns More Rows Than Expected

### Interviewer

You expected 10,000 rows but received 50,000.

### Answer

I would check:

```text
1. Duplicate keys
2. One-to-many joins
3. Many-to-many joins
4. Missing join conditions
5. Incorrect join columns
6. Join filters
```

Example:

```text
Customer
1 row

Orders
5 rows

JOIN result
1 × 5 = 5 rows
```

---

# Scenario 10: Find Changed Records

```sql
SELECT S.*
FROM Source S
JOIN Target T
    ON S.CustomerID = T.CustomerID
WHERE
       COALESCE(S.Name, '') <> COALESCE(T.Name, '')
    OR COALESCE(S.Salary, 0) <> COALESCE(T.Salary, 0);
```

---

# Scenario 11: Find New Records

```sql
SELECT S.*
FROM Source S
LEFT JOIN Target T
    ON S.CustomerID = T.CustomerID
WHERE T.CustomerID IS NULL;
```

---

# Scenario 12: Data Reconciliation

A typical Data Engineering reconciliation:

```text
SOURCE
  ↓
Count
  ↓
Target
  ↓
Count

Then:

Business Key
+
Column Comparison
+
Aggregate Comparison
+
Duplicate Check
```

Example:

```sql
SELECT COUNT(*)
FROM Source;
```

```sql
SELECT COUNT(*)
FROM Target;
```

---

# Scenario 13: NULL Values in Source

### Interviewer

Source contains NULL salary.

What will you do?

### Answer

First determine the business requirement.

If NULL should become 0:

```sql
COALESCE(Salary, 0)
```

If NULL means unknown, preserve NULL.

Never automatically convert NULL without understanding the business meaning.

---

# Scenario 14: Duplicate Business Keys

### Interviewer

How do you handle duplicate business keys?

### Answer

```text
1. Identify duplicate keys
2. Determine correct record
3. Use ROW_NUMBER
4. Keep latest/valid record
5. Reject or quarantine invalid records
6. Add data-quality validation
```

---

# Scenario 15: Latest Salary Record

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY EmployeeID
            ORDER BY EffectiveDate DESC
        ) AS rn
    FROM SalaryHistory
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

# Scenario 16: Find Missing Dates

Use a calendar table.

```sql
SELECT
    C.CalendarDate
FROM Calendar C
LEFT JOIN Sales S
    ON C.CalendarDate = S.SaleDate
WHERE S.SaleDate IS NULL;
```

---

# Scenario 17: Monthly Sales Growth

```sql
WITH Monthly AS
(
    SELECT
        SaleMonth,
        SUM(Amount) AS Sales
    FROM Sales
    GROUP BY SaleMonth
),
Comparison AS
(
    SELECT
        *,
        LAG(Sales) OVER
        (
            ORDER BY SaleMonth
        ) AS PreviousSales
    FROM Monthly
)
SELECT
    SaleMonth,
    Sales,
    PreviousSales,
    Sales - PreviousSales AS Difference
FROM Comparison;
```

---

# Scenario 18: Find Top 3 Customers

```sql
WITH CustomerSales AS
(
    SELECT
        CustomerID,
        SUM(Amount) AS TotalSales
    FROM Sales
    GROUP BY CustomerID
),
Ranked AS
(
    SELECT
        *,
        DENSE_RANK() OVER
        (
            ORDER BY TotalSales DESC
        ) AS rn
    FROM CustomerSales
)
SELECT *
FROM Ranked
WHERE rn <= 3;
```

---

# Scenario 19: Source-to-Target Reconciliation

```sql
SELECT
    S.BusinessKey,
    S.Amount AS SourceAmount,
    T.Amount AS TargetAmount
FROM Source S
FULL OUTER JOIN Target T
    ON S.BusinessKey = T.BusinessKey
WHERE
       S.BusinessKey IS NULL
    OR T.BusinessKey IS NULL
    OR COALESCE(S.Amount, 0)
       <> COALESCE(T.Amount, 0);
```

This can identify:

```text
Source-only records
Target-only records
Value mismatches
```

---

# Scenario 20: Idempotent Data Load

### Interviewer

How do you make a pipeline idempotent?

### Answer

An idempotent pipeline should produce the same final result even if the same batch is executed again.

Typical techniques:

```text
Business keys
MERGE / UPSERT
Deduplication
Watermarks
Batch IDs
Load IDs
Staging tables
Deterministic transformations
```

Example concept:

```text
Source
  ↓
Staging
  ↓
Deduplicate
  ↓
MERGE by Business Key
  ↓
Target
```

---

# 29. FINAL REVISION CHECKLIST

## SQL Basics

```text
[ ] SELECT
[ ] WHERE
[ ] DISTINCT
[ ] ORDER BY
[ ] GROUP BY
[ ] HAVING
[ ] CASE
[ ] NULL
[ ] COALESCE
[ ] NULLIF
```

---

## Joins

```text
[ ] INNER JOIN
[ ] LEFT JOIN
[ ] RIGHT JOIN
[ ] FULL JOIN
[ ] CROSS JOIN
[ ] SELF JOIN
```

---

## Subqueries

```text
[ ] Scalar
[ ] Single-row
[ ] Multi-row
[ ] Correlated
[ ] EXISTS
[ ] NOT EXISTS
[ ] IN
[ ] NOT IN
```

---

## CTE

```text
[ ] Basic CTE
[ ] Multiple CTE
[ ] Recursive CTE
[ ] CTE vs Subquery
```

---

## Window Functions

```text
[ ] ROW_NUMBER
[ ] RANK
[ ] DENSE_RANK
[ ] LAG
[ ] LEAD
[ ] SUM OVER
[ ] AVG OVER
[ ] COUNT OVER
[ ] NTILE
[ ] FIRST_VALUE
[ ] LAST_VALUE
```

---

## Advanced SQL

```text
[ ] Duplicate removal
[ ] Latest record
[ ] Top N
[ ] Nth highest salary
[ ] Running total
[ ] Moving average
[ ] Month-over-month
[ ] Consecutive dates
[ ] Missing dates
[ ] Gaps and Islands
[ ] Source-target comparison
```

---

## Database Theory

```text
[ ] Transactions
[ ] ACID
[ ] COMMIT
[ ] ROLLBACK
[ ] SAVEPOINT
[ ] Concurrency
[ ] Dirty Read
[ ] Non-repeatable Read
[ ] Phantom Read
[ ] Lost Update
[ ] Locks
[ ] Deadlocks
[ ] Isolation Levels
```

---

## Performance

```text
[ ] Indexes
[ ] Clustered Index
[ ] Non-Clustered Index
[ ] Composite Index
[ ] Covering Index
[ ] SARGability
[ ] Execution Plan
[ ] Table Scan
[ ] Query Optimization
[ ] Statistics
```

---

## Data Engineering

```text
[ ] Incremental Load
[ ] Watermark
[ ] CDC
[ ] Deduplication
[ ] Latest Record
[ ] Source-Target Reconciliation
[ ] Data Quality
[ ] Late Arriving Data
[ ] Idempotency
[ ] SCD Concepts
```

---

# ⭐ MOST IMPORTANT QUESTIONS TO PRACTICE

If interview is tomorrow, prioritize these:

```text
1. Second highest salary
2. Nth highest salary
3. Top 3 employees per department
4. Duplicate records
5. Remove duplicates
6. Latest record per ID
7. Employees above department average
8. ROW_NUMBER vs RANK vs DENSE_RANK
9. LAG vs LEAD
10. Running total
11. CTE
12. Recursive CTE
13. Correlated subquery
14. EXISTS vs IN
15. UNION vs UNION ALL
16. WHERE vs HAVING
17. NULL handling
18. Source-target reconciliation
19. Incremental load
20. ACID
21. Isolation levels
22. Dirty read
23. Non-repeatable read
24. Phantom read
25. Deadlock
26. Indexing
27. Clustered vs non-clustered
28. Composite index
29. Query execution order
30. Query optimization
```

---

# 🎯 INTERVIEW ANSWERING FORMULA

For every SQL theory question:

```text
DEFINITION
     ↓
SIMPLE EXAMPLE
     ↓
SQL QUERY
     ↓
REAL-WORLD USE CASE
     ↓
PERFORMANCE / LIMITATION
```

Example:

### Question

What is a CTE?

### Answer

A CTE stands for Common Table Expression. It allows us to define a
temporary named result set that can be referenced by the main query.

I mainly use CTEs for:

- Complex SQL
- Breaking logic into steps
- Deduplication
- Window functions
- Recursive hierarchies

Example:

```sql
WITH Ranked AS
(
    SELECT
        *,
        ROW_NUMBER() OVER
        (
            PARTITION BY EmployeeID
            ORDER BY UpdatedDate DESC
        ) AS rn
    FROM Employee
)
SELECT *
FROM Ranked
WHERE rn = 1;
```

---

# 🚀 DATA ENGINEER SQL MINDSET

Do not only think:

> "Can I write the query?"

Think:

```text
Can it scale?
     ↓
How much data?
     ↓
Are join keys correct?
     ↓
Are there duplicates?
     ↓
Can an index help?
     ↓
Can I avoid unnecessary scans?
     ↓
How will I handle NULL?
     ↓
How will I handle late data?
     ↓
How will I validate the result?
     ↓
How will I make the pipeline idempotent?
```

---

# SQL INTERVIEW PREPARATION STATUS

```text
SQL Fundamentals             ✅
DDL / DML / DQL / DCL / TCL  ✅
Keys & Constraints            ✅
Joins                         ✅
Aggregations                  ✅
Subqueries                    ✅
Correlated Subqueries         ✅
CTE                           ✅
Recursive CTE                 ✅
Window Functions              ✅
NULL Handling                 ✅
CASE                          ✅
Set Operators                 ✅
Date / String                 ✅
Duplicate Handling            ✅
Transactions                  ✅
ACID                          ✅
Concurrency                   ✅
Isolation Levels              ✅
Locks                         ✅
Deadlocks                     ✅
Indexing                      ✅
Normalization                 ✅
OLTP / OLAP                   ✅
Execution Order               ✅
Query Optimization            ✅
100 SQL Questions             ✅
Data Engineer Scenarios       ✅
```

---

# NOTE

Stored Procedures are intentionally excluded from this SQL preparation.

They will be covered separately using a dedicated practice script.

---

# FINAL GOAL

After completing this README, I should be able to:

```text
UNDERSTAND THE THEORY
        +
WRITE THE SQL
        +
EXPLAIN THE SQL
        +
DEBUG THE SQL
        +
OPTIMIZE THE SQL
        +
APPLY SQL TO DATA ENGINEERING SCENARIOS
```

**Target Roles:**

```text
Azure Data Engineer
Data Engineer
Big Data Engineer
Databricks Engineer
ETL Developer
Data Platform Engineer
Analytics Engineer
```

---

# END OF SQL INTERVIEW PREPARATION
```

**Important:** this is the format you should paste into `README.md`—including the outer ```markdown code fence only if you're copying it from this answer into another Markdown/code editor. **Do not put the outer ` ```markdown ` and final ` ``` ` inside the actual README file**, otherwise GitHub will render the entire README as a code block.

For your preparation, I would also keep a **separate `100-questions.sql`** containing only the queries so you can actually run them one by one in your SQL environment, while this README remains your theory + interview revision sheet.
