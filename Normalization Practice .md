?  Case1: Company system – UNF table 
----------------------------------------------------------

|EmployeeID | EmployeeName | Department| Projects|  Manager |
|-----------|--------------|------------|--------|-----------|
|E001| Ahmed| IT| P101:Website, P102:Mobile App| Eng. Khalid |
|E002| Salim| HR| P103:Recruitment| Ms. Amal| 
|E003| Aisha| IT |P102:Mobile App, P104:Database Upgrade| Eng. Khalid 

 ------------------
Since there are duplicate values ??in this table, I will use the conversion method to the _**First Normal Form (1NF)**_

*First table:

|EmployeeID | EmployeeName | Department|  Manager |
|-----------|--------------|------------|-----------|
|E001| Ahmed| IT| Eng. Khalid |
|E002| Salim| HR|  Ms. Amal| 
|E003| Aisha| IT | Eng. Khalid 

* Second table:

|EmployeeID |Projects|
|-----------|--------|
|E001|P101:Website|
|E001|P102:Mobile App|
|E002|P103:Recruitment|
|E003|P102:Mobile App|
|E003|P104:Database Upgrade|

------------------------------------------------














?  Case 2: University System – UNF Table
---------------------------------------------
|BookingID| PassengerName| Flights| SeatNumbers| PaymentMethod|
|---------|--------------|--------|------------|--------------|
|B001 |Salem |F101:Muscat-Dubai, F102:Dubai-London |12A, 14C |Credit Card|
|B002| Fatma| F103:Muscat-Istanbul| 10B| PayPal |
|B003| Zayed| F104:Istanbul-Paris,| F105:Paris-Oslo 9A,| 13A |Credit Card |
 
 