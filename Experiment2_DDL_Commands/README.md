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
--<img width="843" height="383" alt="image" src="https://github.com/user-attachments/assets/90493da9-84bd-4c41-9bcd-4dc8cd250f90" />


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

<img width="1275" height="312" alt="image" src="https://github.com/user-attachments/assets/eff26862-beac-4de0-804e-3c77f9dd33eb" />


**Question 2**
---
-- <img width="666" height="180" alt="image" src="https://github.com/user-attachments/assets/2fb1bfba-b03d-4b8a-82be-b957176a1710" />


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

<img width="1321" height="287" alt="image" src="https://github.com/user-attachments/assets/4175392f-177a-41e1-8a3e-f24410dd9d10" />


**Question 3**
---
<img width="558" height="287" alt="image" src="https://github.com/user-attachments/assets/bc6a6f74-8725-4517-a5ce-1e9db0e8171e" />


```sql
INSERT INTO Employee(EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary FROM  Former_employees;
```

**Output:**

<img width="1013" height="291" alt="image" src="https://github.com/user-attachments/assets/c6fd752a-64f7-422a-ae5f-0838bf6e466b" />


**Question 4**
---
<img width="1153" height="262" alt="image" src="https://github.com/user-attachments/assets/477b4055-5cc6-4a81-967c-0ef101bce0e7" />


```sql
CREATE TABLE Department
(
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

**Output:**

<img width="1290" height="278" alt="image" src="https://github.com/user-attachments/assets/e4ed77da-9d9a-40cf-a641-a1851ef59b29" />

**Question 5**
---
<img width="1048" height="326" alt="image" src="https://github.com/user-attachments/assets/4f04a0b0-06e7-47eb-a15d-ff15493d78c4" />


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

<img width="1356" height="389" alt="image" src="https://github.com/user-attachments/assets/3b220923-aa14-4f5c-8aad-58144ffba322" />


**Question 6**
---
<img width="1166" height="243" alt="image" src="https://github.com/user-attachments/assets/78d19131-4d07-4efe-948d-c2a92031112c" />

```sql
ALTER TABLE  Student_details ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';

```

**Output:**

<img width="1341" height="233" alt="image" src="https://github.com/user-attachments/assets/25a20ecf-bbc3-4948-a22c-af132e18c28e" />


**Question 7**
---
<img width="758" height="379" alt="image" src="https://github.com/user-attachments/assets/7331a16b-c469-463a-a335-3b1f28a1d46f" />


```sql
INSERT INTO Books(ISBN ,Title ,Author) VALUES ('978-6655443321'  , 'Big Data Analytics' ,'Karen Adams');

```

**Output:**

<img width="1102" height="304" alt="image" src="https://github.com/user-attachments/assets/ee9626c3-b647-4668-a8fa-0b44a88eb385" />

**Question 8**
---
<img width="857" height="320" alt="image" src="https://github.com/user-attachments/assets/2d72ac4d-7b86-4101-b891-17ef452fd221" />


```sql
ALTER TABLE Student_details ADD COLUMN  ParentsNumber number;
ALTER TABLE Student_details ADD COLUMN  Adhar_Number number;
```

**Output:**

<img width="1284" height="339" alt="image" src="https://github.com/user-attachments/assets/bdf0ca26-bebd-4aa5-94a3-93428f2490f3" />


**Question 9**
---
<img width="943" height="299" alt="image" src="https://github.com/user-attachments/assets/48f89433-d6cd-4d88-baeb-f5825d69d5ae" />


```sql
ALTER table Employees ADD COLUMN  Date_of_joining Date ;
ALTER table Employees RENAME Column  job_title to Designation;
```

**Output:**

<img width="1306" height="327" alt="image" src="https://github.com/user-attachments/assets/db2d6e91-658f-470a-85a3-6cb5c020f90d" />


**Question 10**
---

<img width="1122" height="279" alt="image" src="https://github.com/user-attachments/assets/93bd82bd-1090-45fc-bac1-c7ce772a2ce6" />


```sql
Insert into Books( ISBN, Title, Author, Publisher, YearPublished)
select ISBN, Title, Author, Publisher, YearPublished from  Out_of_print_books;
```

**Output:**

<img width="1319" height="249" alt="image" src="https://github.com/user-attachments/assets/3d4c2cc7-075d-4850-8f46-2bf661ba5d23" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
