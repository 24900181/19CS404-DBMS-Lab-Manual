# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE
```sql
CREATE TABLE Employees
(
    EmployeeID INTEGER ,
    FirstName TEXT ,
    LastName TEXT,
    HireDate DATE
);
```

**Output:**

<img width="1426" height="368" alt="image" src="https://github.com/user-attachments/assets/0250c185-f119-4851-86ea-f4c745f85506" />


**Question 2**
---
-- 
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
CREATE TABLE Bonuses
(
    BonusID  INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount REAL CHECK (BonusAmount>0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)

);
```

**Output:**

<img width="1379" height="298" alt="image" src="https://github.com/user-attachments/assets/364386b9-bfb6-462d-bda5-fe242967488c" />


**Question 3**
---
-- Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
INSERT INTO Employee(EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary FROM  Former_employees;
```

**Output:**

<img width="1404" height="302" alt="image" src="https://github.com/user-attachments/assets/e96d4579-0359-4964-a91e-3929c507dab3" />


**Question 4**
---
-- Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
CREATE TABLE Department
(
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

**Output:**

<img width="1309" height="302" alt="image" src="https://github.com/user-attachments/assets/390fb7ed-f4fd-4cb6-8b80-7438d78f9b8f" />


**Question 5**
---
--Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
CREATE TABLE Employees
(
   EmployeeID INTEGER PRIMARY KEY,
   FirstName  NOT NULL,
   LastName NOT NULL,
   Email UNIQUE,
   Salary CHECK(Salary>0),
   DepartmentID INTEGER,
   FOREIGN KEY(DepartmentID) REFERENCES Departments(DepartmentID)
   
);
```

**Output:**
<img width="1327" height="395" alt="image" src="https://github.com/user-attachments/assets/ae85acf5-597d-414c-a558-79391f54a530" />


**Question 6**
---
--Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'

```sql
ALTER TABLE  Student_details ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';
```

**Output:**

<img width="1329" height="283" alt="image" src="https://github.com/user-attachments/assets/78090471-bf69-40eb-8bda-4274c4f42dfc" />


**Question 7**
---
--Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

ISBN             Title                 Author
---------------  --------------------  ---------------
978-6655443321   Big Data Analytics    Karen Adams

Note: The Publisher and Year columns will use their default values.
 

```sql
INSERT INTO Books(ISBN ,Title ,Author) VALUES ('978-6655443321'  , 'Big Data Analytics' ,'Karen Adams');
```

**Output:**

<img width="1284" height="299" alt="image" src="https://github.com/user-attachments/assets/8dd86e41-8930-48de-81fb-e36a9bf0c42c" />


**Question 8**
---
--In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT

```sql
Insert into Employee(EmployeeID , Name  , Position ,Department,Salary)
Values('5 ','George Clark','Consultant',null,null);
Insert into Employee(EmployeeID , Name  , Position ,Department,Salary)
Values('7' ,'Noah Davis', 'Manager', 'HR'  ,'60000');
Insert into Employee(EmployeeID , Name , Position ,Department,Salary)
Values('8','Ava Miller','Consultant' , 'IT',null);

```

**Output:**

<img width="1383" height="287" alt="image" src="https://github.com/user-attachments/assets/a5c9a90d-1f51-48bf-8239-8dc935341a0b" />


**Question 9**
---
-- Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.

```sql
ALTER TABLE Student_details ADD COLUMN  ParentsNumber number;
ALTER TABLE Student_details ADD COLUMN  Adhar_Number number;
```

**Output:**

<img width="1362" height="374" alt="image" src="https://github.com/user-attachments/assets/38744ff5-5d3a-48fc-9f50-4d1ef62173b7" />


**Question 10**
---
-- create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
create table jobs
(
   job_id integer primary key,
   job_title varchar(50) default '',
   min_salary int default 8000,
   max_salary default null
)
```

**Output:**
<img width="1480" height="254" alt="image" src="https://github.com/user-attachments/assets/2bac1c4d-dc5b-4cda-b20f-50a9a1a5b7c5" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
