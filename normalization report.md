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
