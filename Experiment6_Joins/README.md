# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1112" height="608" alt="image" src="https://github.com/user-attachments/assets/40abffe9-2c53-4956-ab20-05b0a7d0abbe" />


```sql
SELECT 
    customer.cust_name AS "Customer Name", 
    customer.city AS "city", 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    customer
JOIN 
    salesman
ON 
    customer.salesman_id = salesman.salesman_id
WHERE 
    salesman.commission > 0.12;
```

**Output:**

<img width="885" height="467" alt="image" src="https://github.com/user-attachments/assets/286d7307-442e-4951-98b6-2cbcdec28aca" />


**Question 2**
---
<img width="1333" height="448" alt="image" src="https://github.com/user-attachments/assets/3d0abc97-4732-405e-8472-78235cd023ca" />


```sql
SELECT 
    patients.date_of_birth, 
    appointments.*
FROM 
    patients
JOIN 
    appointments
ON 
    patients.patient_id = appointments.patient_id
WHERE 
    patients.first_name = 'Alice';
```

**Output:**

<img width="1143" height="220" alt="image" src="https://github.com/user-attachments/assets/39459c54-da5f-4078-94d3-40d37342b7db" />


**Question 3**
---
<img width="890" height="655" alt="image" src="https://github.com/user-attachments/assets/7df7e778-cb03-4320-a1dc-b6efd24acdbf" />

```sql
SELECT 
    orders.ord_no, 
    orders.ord_date, 
    orders.purch_amt, 
    customer.cust_name AS "Customer Name", 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    orders
JOIN 
    customer ON orders.customer_id = customer.customer_id
JOIN 
    salesman ON orders.salesman_id = salesman.salesman_id;
```

**Output:**

<img width="1318" height="761" alt="image" src="https://github.com/user-attachments/assets/0edcb08b-fcd7-43de-995c-2e198a2cd5cb" />


**Question 4**
---
<img width="1215" height="385" alt="image" src="https://github.com/user-attachments/assets/f0987516-d0e7-40d8-a4d7-53a47afee0a9" />


```sql
SELECT 
    customer.cust_name, 
    customer.city, 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.city AS "city"
FROM 
    customer
JOIN 
    salesman ON customer.salesman_id = salesman.salesman_id
WHERE 
    customer.grade < 300
ORDER BY 
    customer.customer_id ASC;
```

**Output:**

<img width="1026" height="462" alt="image" src="https://github.com/user-attachments/assets/dea210e4-3a8f-4662-acd2-5f0b8e2c4f25" />


**Question 5**
---
<img width="1297" height="273" alt="image" src="https://github.com/user-attachments/assets/2af5850f-a570-4769-9805-ad05ff1b054a" />


```sql
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';
```

**Output:**

<img width="270" height="267" alt="image" src="https://github.com/user-attachments/assets/8da9f182-691e-4727-8fe3-6b8b6eafe066" />


**Question 6**
---<img width="971" height="259" alt="image" src="https://github.com/user-attachments/assets/aa97bd45-ceff-4560-beb1-b73214be0630" />


```sql
SELECT 
    c.cust_name
FROM 
    customer AS c
LEFT JOIN 
    orders AS o ON c.customer_id = o.customer_id;
```

**Output:**

<img width="274" height="759" alt="image" src="https://github.com/user-attachments/assets/6d993eea-1fa7-4918-bb58-f52b46aee52e" />


**Question 7**
---
<img width="1560" height="360" alt="image" src="https://github.com/user-attachments/assets/ef4944a5-f3b8-4c3b-8c76-aa9f57c4479d" />


```sql
SELECT 
    p.first_name AS patient_name, 
    t.*
FROM 
    patients AS p
INNER JOIN 
    test_results AS t ON p.patient_id = t.patient_id;

```

**Output:**

<img width="1370" height="367" alt="image" src="https://github.com/user-attachments/assets/ccb6fe37-9d3b-463c-87a5-5cfa9e46c166" />

**Question 8**
---
<img width="1154" height="459" alt="image" src="https://github.com/user-attachments/assets/6c7f89a7-f1fa-4945-8e22-764bda22a45d" />


```sql
SELECT 
    c.cust_name, 
    c.city AS city, 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city
FROM 
    customer c
LEFT JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

<img width="1202" height="657" alt="image" src="https://github.com/user-attachments/assets/265133a6-5612-4e95-aa48-83dd12a2a879" />


**Question 9**
---
<img width="1300" height="435" alt="image" src="https://github.com/user-attachments/assets/5cd3a9bb-03f9-4d64-93be-b33c70bb5e68" />


```sql
SELECT 
    p.admission_date, 
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s 
ON 
    p.patient_id = s.patient_id;
```

**Output:**

<img width="555" height="368" alt="image" src="https://github.com/user-attachments/assets/cd738623-e860-4567-9bc8-c0002ad4e3b9" />


**Question 10**
---
<img width="1041" height="464" alt="image" src="https://github.com/user-attachments/assets/78e1dfdd-09a3-434a-84df-fab0898d2ee4" />


```sql
-SELECT 
    c.cust_name AS "Customer Name", 
    c.city, 
    s.name AS "Salesman", 
    s.commission
FROM 
    customer c
JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1037" height="660" alt="image" src="https://github.com/user-attachments/assets/81a73cab-e6fa-4fd7-8836-c9d3c4be7c06" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
