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
--Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

```
-- UPDATE Suppliers
set address='58 Lakeview, Magnolia'
where supplier_id=5;

```

**Output:**

<img width="1247" height="307" alt="image" src="https://github.com/user-attachments/assets/f787078b-7c54-4896-bb74-0e544714a822" />


**Question 2**
---
-- Write a SQL statement to double the availability of the product with product_id 1.

```
update products
set availability=availability*2
where product_id=1;
```


**Output:**

<img width="1212" height="233" alt="image" src="https://github.com/user-attachments/assets/af066aaf-c6db-4ea5-a86b-e5db7c95300d" />


**Question 3**
---
-- Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

```
update SALES
set total_sell_price=quantity*sell_price
where product_id=10;

```

**Output:**

<img width="1241" height="353" alt="image" src="https://github.com/user-attachments/assets/e4cf2d58-b97f-4f8c-8365-c1546e1f538d" />


**Question 4**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```

DELETE FROM Customer
where GRADE<>3;

```

**Output:**

<img width="1010" height="541" alt="image" src="https://github.com/user-attachments/assets/7a58cfb8-fbdb-4bcb-9523-64c36bf708cf" />


**Question 5**
---
--Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

```

DELETE FROM Doctors
where specialization='Pediatrics' and first_name='Michael';

```

**Output:**

<img width="1186" height="327" alt="image" src="https://github.com/user-attachments/assets/62149cd9-0ea7-43e1-aa57-a1b172cfea40" />


**Question 6**
---
--Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

```

DELETE FROM Customer 
where GRADE<2;

```

**Output:**

<img width="721" height="488" alt="image" src="https://github.com/user-attachments/assets/9249a5d2-0e80-405e-a06d-5c2a252f80ca" />

**Question 7**
---
-- Write a SQL query to label rows in the Calculations table as 'Even' if value1 is even, otherwise 'Odd'.

```
SELECT id,value1,
case when (value1%2=0) THEN 'Even' else 'Odd'
end as parity
from Calculations;
```

**Output:**

<img width="858" height="425" alt="image" src="https://github.com/user-attachments/assets/b6a2bc53-8f92-4dc2-b18d-1b7a18c9aded" />


**Question 8**
---
--Write a SQL query to find all employees who were hired in the year 2022 from emp table.

```
SELECT * from emp
where hiredate like '%2022%';
```

**Output:**

<img width="1238" height="275" alt="image" src="https://github.com/user-attachments/assets/c12e3986-7bb9-453e-810f-fccd63a989d5" />


**Question 9**
---
-- Write a query to fetch the number of employees working in the department ‘HR’.

```

SELECT COUNT(*) 
from EmployeeInfo
where department='HR';

```

**Output:**

<img width="632" height="205" alt="image" src="https://github.com/user-attachments/assets/17d215fe-4c24-49f6-a2e1-c2bbed258a9a" />


**Question 10**
---
--Write a SQL query to calculate the discounted price for products where the discount percentage is greater than 0, and order the results by discounted_price in ascending order. Return product_id, original_price, discount_percentage, and discounted_price.

```
SELECT product_id,original_price,discount_percentage,original_price*(1-discount_percentage) as discounted_price
from Products
where discount_percentage>0 
ORDER BY discounted_price ASC;
```

**Output:**

<img width="1208" height="228" alt="image" src="https://github.com/user-attachments/assets/faa17a1d-fc51-4e27-96de-9311927984b2" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
