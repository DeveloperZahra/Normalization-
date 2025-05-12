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

