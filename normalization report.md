<h1>❖ Normalization Report</h>

 ------------------------------------------------
🔸 Normalization is the process of organizing data in a database to minimize redundancy and improve data integrity. 
It involves dividing large tables into smaller, related tables and defining relationships between them.

🔸Types of Normalization:

1) 1NF – First Normal Form

🔹Definition:

A relation is in 1NF if:

All attributes contain only atomic (indivisible) values.

There are no repeating groups or arrays.

 🔹 Use Case:

Apply 1NF when your table contains lists or multi-valued attributes.

🔹Before  1NF:


| StudentID | Name  | Courses            |
| --------- | ----- | ------------------ |
| 101       | zahra | Math, English      |
| 102       | sara  | Physics, Chemistry |


🔹After 1NF:

| StudentID | Name  | Course    |
| --------- | ----- | --------- |
| 101       | zahra | Math      |
| 101       | zahra | English   |
| 102       | sara  | Physics   |
| 102       | sara  | Chemistry |

---------------------------------------------
2)  2NF – Second Normal Form

🔹Definition:

A relation is in 2NF if:

It is in 1NF

No partial dependency exists (non-key attributes depend on the entire primary key, not just a part of it)

🔹 Use Case:

Apply 2NF when you have a composite primary key and some fields depend only on part of that key.


🔹Before  2NF:

| OrderID | ProductID | ProductName | Quantity |
| ------- | --------- | ----------- | -------- |
| 5001    | P01       | saif        |    2     |
| 5001    | P02       | Anas        |    3     |

Here, ProductName depends only on ProductID, not on (OrderID, ProductID).


🔹 After 2NF (split into  2 tables):

   * OrderDetails Table
	
| OrderID | ProductID | Quantity |
| ------- | --------- | -------- |
| 5001    | P01       | 2        |
| 5001    | P02       | 3        |

 * Products Table
	
| ProductID | ProductName |
| --------- | ----------- |
| P01       | saif        |
| P02       | anas        |

-----------------------------------
3)  3NF – Third Normal Form
	
🔹Definition:

A relation is in 3NF if:

It is in 2NF

There is no transitive dependency (non-key attribute depends only on the primary key, not on another non-key attribute)

🔹Use Case:

Apply 3NF when a non-key attribute depends on another non-key attribute.

🔹Before  3NF:

| StudentID | StudentName | Department | DepartmentLocation |
| --------- | ----------- | ---------- | ------------------ |
| 1001      | Ghassan      | CS         | Building A        |

Here, DepartmentLocation depends on Department, not on StudentID.

🔹 After 3NF:

* Students Table

| StudentID | StudentName | Department |
| --------- | ----------- | ---------- |
| 1001      |   Ghassan   | CS         | 

* Departments Table

| Department | DepartmentLocation |
| ---------- | ------------------ |
| CS         | Building A         |

---------------------------------------
4) BCNF – Boyce-Codd Normal Form

🔹Definition:

A relation is in BCNF if:

It is in 3NF

Every determinant is a candidate key

🔹 Use Case:

Use BCNF when non-prime attributes determine other fields but are not candidate keys.

🔹 Before BCNF: 

| Professor | Subject | Department |
| --------- | ------- | ---------- |
| Smith     | DBMS    | CS         |
| Smith     | OS      | CS         |

Here, Professor → Department, but Professor is not a candidate key.

🔹After BCNF: 

* ProfessorDept Table

| Professor | Department |
| --------- | ---------- |
| Smith     | CS         |


* Teaching Table

| Professor | Subject |
| --------- | ------- |
| Smith     | DBMS    |
| Smith     | OS      |

----------------------------------

5) 4NF – Fourth Normal Form

🔹Definition:

A relation is in 4NF if:

It is in BCNF

It has no multi-valued dependencies

🔹Use Case:

Apply 4NF when multiple independent multi-valued facts exist in the same table.

 🔹 Before 4NF:

 | Student | Course  | Hobby    |
| ------- | ------- | -------- |
| John    | Math    | Painting |
| John    | Math    | Chess    |
| John    | Physics | Painting |
| John    | Physics | Chess    |

  🔹 After 4NF:
	
* StudentCourses Table
	
| Student | Course  |
| ------- | ------- |
| John    | Math    |
| John    | Physics |

* StudentHobbies Table

| Student | Hobby    |
| ------- | -------- |
| John    | Painting |
| John    | Chess    |

-------------------------------------

6) 5NF – Fifth Normal Form (PJNF)
 
🔹Definition:

A relation is in 5NF if:

It is in 4NF

It has no join dependencies that are not implied by candidate keys

🔹 Use Case:

Use 5NF when reconstructing data from decomposed tables causes lossless join issues.

🔹 Before 5NF (Conceptual)

Imagine a table that stores information like:

Model

Feature

Supplier

Data combinations can be misleading without careful normalization.

----------------------------------------------

🔸 A simple comparison between the types of database normalization

| Normal Form | Key Issue Resolved        | Ensures That...                            |
| ----------- | ------------------------- | ------------------------------------------ |
| 1NF         | Repeating groups          | Atomic values only                         |
| 2NF         | Partial dependencies      | All non-key attributes depend on full PK   |
| 3NF         | Transitive dependencies   | Attributes depend only on the key          |
| BCNF        | Determinant issues        | Determinants must be candidate keys        |
| 4NF         | Multi-valued dependencies | No unrelated multi-valued facts            |
| 5NF         | Join dependencies         | Reconstructable without loss or redundancy |

---------------------------------------------------------
 🔸 De-Normalization:


De-Normalization is the intentional process of introducing redundancy into a database design
by combining tables that were previously separated during normalization.

🔸 Why Apply De-Normalization?

 1. Improved Read Performance
	
Joins between many normalized tables can slow down query performance.

By combining related tables, you reduce the number of joins needed.

 2. Simpler Queries
	
Easier for developers or reporting tools to retrieve data from fewer tables.

 3. Faster Reporting
	
Especially useful in OLAP systems (data warehousing) where reads are more frequent than writes.

 4. Precomputed Data
	
Storing derived or aggregated data (e.g., total sales per month) avoids recalculating every time.

 🔸 When to Apply De-Normalization?

 Apply de-normalization only after normalization and when:

 | Condition                                 | Explanation                                            |
| ----------------------------------------- | ------------------------------------------------------ |
| **Read-heavy workloads**                  | In systems with many SELECT operations and few updates |
| **Performance bottlenecks**               | Queries are too slow due to multiple joins             |
| **Data is rarely updated**                | Redundancy is acceptable if data doesn't change often  |
| **Data warehousing or reporting systems** | OLAP environments benefit from denormalized structures |

🔸 Example: Before vs. After De-Normalization

🔹 Normalized Design

* Orders Table

| OrderID | CustomerID | Date       |
| ------- | ---------- | ---------- |
| 101     | C01        | 2024-01-01 |

* Customers Table

| CustomerID | Name     | City     |
| ---------- | -------- | -------- |
| C01        | John Doe | New York |


Query to get customer city: Requires a JOIN between Orders and Customers.

🔹 De-Normalized Design

* Orders Table

| OrderID | CustomerID | CustomerName | City     | Date       |
| ------- | ---------- | ------------ | -------- | ---------- |
| 101     | C01        | John Doe     | New York | 2024-01-01 |

Now, the customer’s name and city are stored directly in the orders table — no join needed.
