❖  Case1: Company system – UNF table 
----------------------------------------------------------

|EmployeeID | EmployeeName | Department| Projects|  Manager |
|-----------|--------------|------------|--------|-----------|
|E001| Ahmed| IT| P101:Website, P102:Mobile App| Eng. Khalid |
|E002| Salim| HR| P103:Recruitment| Ms. Amal| 
|E003| Aisha| IT |P102:Mobile App, P104:Database Upgrade| Eng. Khalid 

 ------------------
 there are duplicate values ​​in this table, I will use the conversion method to the _**First Normal Form (1NF)**_

After 1NF (split into  2 tables):

1)

|EmployeeID | EmployeeName | Department|  Manager |
|-----------|--------------|------------|-----------|
|E001| Ahmed| IT| Eng. Khalid |
|E002| Salim| HR|  Ms. Amal| 
|E003| Aisha| IT | Eng. Khalid 

2)

|EmployeeID |Projects|
|-----------|--------|
|E001|P101:Website|
|E001|P102:Mobile App|
|E002|P103:Recruitment|
|E003|P102:Mobile App|
|E003|P104:Database Upgrade|

------------------------------------------------

❖  Case 2: University System – UNF Table
---------------------------------------------
|StudentID| StudentName| Department| Courses Enrolled |Advisor |
|---------|------------|-----------|-------------------|--------|
|S001| Reem| CS |C101:DB, C102:AI |Dr. Omar |
|S002| Tariq| Business |C103:Marketing |Dr. Sarah |
|S003| Noura| CS |C101:DB, C104:Cybersecurity| Dr. Omar |
 
 
  there are duplicate values ​​in this table, I will use the conversion method to the _**First Normal Form (1NF)**_

After 1NF (split into  2 tables):

1)

|StudentID| StudentName| Department|Advisor |
|----------|-----------|-----------|----------|
|S001| Reem| CS |Dr. Omar |
|S002| Tariq| Business |Dr. Sarah |
|S003| Noura| CS |Dr. Omar |

2)

|StudentID| Courses Enrolled |
|---------|------------------|
|S001|C101:DB|
|S001|C102:AI|
|S002|C103:Marketing|
|S003|C101:DB|
|S003|C104:Cybersecurity|

----------------------------------------
  Case 3: Airline System – UNF Table 
  --------------------------------------------

|BookingID| PassengerName| Flights| SeatNumbers | PaymentMethod |
|---------|---------------|---------------|----------|------------|
|B001 |Salem |F101:Muscat-Dubai, F102:Dubai-London |12A, 14C| Credit Card|
|B002| Fatma| F103:Muscat-Istanbul| 10B| PayPal| 
|B003| Zayed| F104:Istanbul-Paris, F105:Paris-Oslo |9A, 13A |Credit Car|

 there are duplicate values ​​in this table, I will use the conversion method to the _**First Normal Form (1NF)**_

After 1NF (split into  3 tables):

1)

|BookingID| PassengerName|PaymentMethod |
|---------|--------------|--------------|
|B001 |Salem |Credit Card|
|B002| Fatma| PayPal| 
|B003| Zayed|Credit Car|

2)

|BookingID|Flights|
|----------|--------|
|B001 |F101:Muscat-Dubai|
|B001 |F102:Dubai-London |
|B002| F103:Muscat-Istanbul|
|B003|F104:Istanbul-Paris|
|B003| F105:Paris-Oslo|

3)

|BookingID|SeatNumbers |
|----------|--------|
|B001 |12A|
|B001 |14C|
|B002|10B|
|B003|9A|
|B003|13A|