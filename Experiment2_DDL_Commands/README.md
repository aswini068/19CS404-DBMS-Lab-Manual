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
-- -- Write a SQL Query to change the name of attribute "name" to "first_name" and add mobilenumber as number ,DOB as Date in the table Companies.

```

 ALTER TABLE Companies
rename name to first_name;
ALTER TABLE Companies
ADD COLUMN mobilenumber number;
ALTER TABLE Companies
ADD COLUMN DOB Date;

```

**Output:**
<img width="1246" height="298" alt="image" src="https://github.com/user-attachments/assets/9a57033e-86c6-486b-918b-67f507d83a38" />


**Question 2**
---
-- Create a table named Products with the following constraints: ProductID as INTEGER should be the primary key. ProductName as TEXT should be unique and not NULL. Price as REAL should be greater than 0. StockQuantity as INTEGER should be non-negative.

```
 CREATE TABLE Products
(
ProductID INTEGER primary key,
ProductName TEXT UNIQUE NOT NULL,
Price REAL CHECK(Price>0),
StockQuantity INTEGER CHECK(StockQuantity>0)
);

```

**Output:**

<img width="842" height="156" alt="image" src="https://github.com/user-attachments/assets/cdd93a63-517c-46b1-875e-fa36abca8cca" />


**Question 3**
---
-- Create a table named Products with the following columns:

ProductID as INTEGER ProductName as TEXT Price as REAL Stock as INTEGER

```
CREATE TABLE Products
(
ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);

```

**Output:**

<img width="1267" height="236" alt="image" src="https://github.com/user-attachments/assets/75ef66bf-1213-4704-bc7c-ad1cb882236d" />


**Question 4**
---
-- Insert the following employees into the Employee table:
EmployeeID Name Position Department Salary

2 John Smith Developer IT 75000 3 Anna Bell Designer Marketing 68000

```
INSERT INTO Employee(EmployeeID,Name,Position,Department ,Salary)
values(2,           'John Smith'  ,'Developer'  , 'IT'  ,        75000);
INSERT INTO Employee(EmployeeID,Name,Position,Department ,Salary)
values(3,           'Anna Bell'  ,'Designer'  , 'Marketing'  ,        68000);
```

**Output:**
<img width="1242" height="277" alt="image" src="https://github.com/user-attachments/assets/dbe25d4b-bcd5-42ea-b017-479d741d9b8e" />



**Question 5**
---
--Create a table named Departments with the following columns:

DepartmentID as INTEGER DepartmentName as TEXT

```
CREATE TABLE Departments
(
DepartmentID INTEGER,
DepartmentName TEXT

);

```

**Output:**
<img width="1237" height="275" alt="image" src="https://github.com/user-attachments/assets/acd21ce6-70e1-4cb4-a0fc-f21751d12712" />



**Question 6**
---
-- Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.
EmployeeID Name Position

4 Emily White Analyst

Note: The Department and Salary columns will use their default values.


```
INSERT INTO Employee(EmployeeID,Name,Position)
values(4           ,'Emily White','Analyst');

```

**Output:**

<img width="828" height="236" alt="image" src="https://github.com/user-attachments/assets/5311fb3b-19fa-4b12-b803-4d3c18190fb8" />


**Question 7**
---
-- Create a table named Orders with the following constraints: OrderID as INTEGER should be the primary key. OrderDate as DATE should be not NULL. CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```
CREATE TABLE Orders
(
OrderID INTEGER primary key,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID)
);

```

**Output:**

<img width="621" height="166" alt="image" src="https://github.com/user-attachments/assets/586276b9-f840-4822-85c2-db31ce9eaf5c" />


**Question 8**
---
-- Insert the following students into the Student_details table: RollNo Name Gender Subject MARKS

```
INSERT INTO Student_details(RollNo ,Name    ,    Gender  ,    Subject ,    MARKS)
values(202       ,  'Ella King'  ,'F','Chemistry' ,  87);
INSERT INTO Student_details(RollNo ,Name    ,    Gender  ,    Subject ,    MARKS)
values(203       ,  'James Bond'  ,'M','Literature' ,  78);

```

**Output:**

<img width="1239" height="195" alt="image" src="https://github.com/user-attachments/assets/3cf91aab-cbcc-40d2-ae01-886292e77b41" />


**Question 9**
---

Create a new table named item with the following specifications and constraints: item_id as TEXT and as primary key. item_desc as TEXT. rate as INTEGER. icom_id as TEXT with a length of 4. icom_id is a foreign key referencing com_id in the company table. The foreign key should cascade updates and deletes. item_desc and rate should not accept NULL.

```
CREATE TABLE item
(
item_id TEXT primary key,
item_desc TEXT not null,
rate INTEGER not null,
icom_id TEXT(4),
FOREIGN KEY(icom_id) REFERENCES company(com_id)
on update cascade
on delete cascade
);

```

**Output:**

<img width="1211" height="262" alt="image" src="https://github.com/user-attachments/assets/2ea13adb-0f44-46ad-bf00-817fda59dd9b" />


**Question 10**
---
--Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```
ALTER TABLE Companies
ADD COLUMN designation varchar(50);
ALTER TABLE Companies
ADD COLUMN net_salary number;

```

**Output:**

<img width="1233" height="311" alt="image" src="https://github.com/user-attachments/assets/f1aa1bf7-791f-44f8-a5a1-984ab9cfc896" />




## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
