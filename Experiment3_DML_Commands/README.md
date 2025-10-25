# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
--Write a SQL query to calculate the absolute value of the value1 column from the Calculations table.

cid            name          type       notnull    dflt_value     pk
---------- ----------  ----------  ----------  ----------     ----------
0              id          INTEGER     0                          1
1             value1       REAL        0                          0
2             value2       REAL        0                          0
3            base        INTEGER       0                       0
4           exponent    INTEGER        0                       0
5           number      REAL           0                       0
6           decimal     REAL           0                       0

```sql
select id,value1, ABS(value1) as "absolute_value" from Calculations;
```

**Output:**

<img width="1364" height="295" alt="image" src="https://github.com/user-attachments/assets/e9153dce-50d9-4620-8a96-402e5cfffe04" />


**Question 2**
---
-- Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization


```sql
delete from Doctors where doctor_id=1;
```

**Output:**

<img width="1381" height="271" alt="image" src="https://github.com/user-attachments/assets/35a60c10-66a6-4008-8c60-5442d02ae57f" />


**Question 3**
---
--<img width="772" height="343" alt="image" src="https://github.com/user-attachments/assets/449b29ce-ff49-48e2-a541-c02dcf8fd3de" />


```sql
select name,city from salesman where city="London" or city="Rome";
```

**Output:**

<img width="1219" height="362" alt="image" src="https://github.com/user-attachments/assets/7983bccf-a2be-43e1-9beb-918bf5acd8c3" />


**Question 4**
---
-- Write a query to Select all the records from the EmployeeInfo table, where the departments are either HR or Account.
EmpID   EmpFname  EmpLname   Department   Project    Address          DOB         Gender

1        Sanjay    Mehra        HR          P1     Hyderabad(HYD)   01/12/1976      M

2        Ananya    Mishra      Admin        P2     Delhi(DEL)       02/05/1968      F



```sql
select * from EmployeeInfo where Department="HR" or Department ="Account";
```

**Output:**

<img width="1374" height="251" alt="image" src="https://github.com/user-attachments/assets/69f5bc31-2648-4f60-b211-255806163f99" />


**Question 5**
---
--Write a SQL query to retrieve all employee names in lower case. 

Table name: emp

name        type
----------  ----------
empno       INT
ename       VARCHAR(100)
job         VARCHAR(50)
mgr         INT
hiredate    DATE
sal         DECIMAL(10,2)
comm        DECIMAL(10,2)
deptno      INT

```sql
select lower(ename) as "EmpName" from emp;
```

**Output:**

<img width="1223" height="536" alt="image" src="https://github.com/user-attachments/assets/04cbd767-a0fa-4b95-8823-d23ad65b7a61" />


**Question 6**
---
-- For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)

```sql
update sales set sell_price= sell_price+3 where sale_id=4 ;
update sales set sell_price= sell_price+3 where sale_id in (10,11,12);
```

**Output:**

<img width="1408" height="339" alt="image" src="https://github.com/user-attachments/assets/64168723-fd08-4072-910d-f7bc811e5b83" />


**Question 7**
---
-- Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

```sql
delete from customer where cust_country="India" and cust_city <> "Chennai";
```

**Output:**

<img width="1423" height="502" alt="image" src="https://github.com/user-attachments/assets/6d8f7772-91f2-4df9-a60b-a41491f8bb8f" />


**Question 8**
---
-- Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
update Suppliers set address='58 Lakeview, Magnolia' where supplier_id=5;
```

**Output:**

<img width="1318" height="311" alt="image" src="https://github.com/user-attachments/assets/dc041826-188b-4bf2-b932-d37999ed7721" />

**Question 9**
---
--Write a SQL query to calculate the number of days between the hiredate and a specified date ('2024-12-31') for each employee using the JULIANDAY function from the emp table.

emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT         

```sql
select ename,hiredate, ROUND(JULIANDAY('2024-12-31')-JULIANDAY(Hiredate))as "days_worked" from emp;
```

**Output:**

<img width="1303" height="303" alt="image" src="https://github.com/user-attachments/assets/5f13ba5e-9b68-4585-b1b9-5396ee0e81c2" />


**Question 10**
---
-- Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
Insert into Books( ISBN, Title, Author, Publisher, YearPublished)
select ISBN, Title, Author, Publisher, YearPublished from  Out_of_print_books;
```

**Output:**
<img width="1368" height="231" alt="image" src="https://github.com/user-attachments/assets/472461f3-f165-443d-8652-027fcd02ba11" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
