# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table

```
Medication     AvgDosage
-------------  ----------
Ciprofloxacin  500.0
Doxorubicin    60.0
Ibuprofen      400.0
Levothyroxine  50.0
Lisinopril     10.0
MMR            0.5
Pending        0.0
Prenatal vita  1.0
Sertraline     50.0
Topiramate     25.0
```

```sql
SELECT
  Medication,
  AVG(Dosage) AS AvgDosage
FROM
  Prescriptions
GROUP BY
  Medication;

```

**Output:**

<img width="697" height="745" alt="image" src="https://github.com/user-attachments/assets/63b0187c-f0aa-44a6-8c63-4081bbe1a750" />


**Question 2**
---
How many patients are there in each city?

```
Sample table: Patients Table

Address     TotalPatients
----------  -------------
Berlin      3
Chicago     4
Mexico      3
```

```sql
select Address,count(*)
as TotalPatients
from Patients
group by Address
```

**Output:**

<img width="661" height="396" alt="image" src="https://github.com/user-attachments/assets/5969a8d5-a23d-41f9-a3b8-eedf9a114b42" />


**Question 3**
---
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

```
PatientID   AvgMedications
----------  --------------
4           5
6           1
7           1
8           3

```
```sql
SELECT PatientID,COUNT(*) AS 
AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

<img width="679" height="614" alt="image" src="https://github.com/user-attachments/assets/1daf4689-fe26-4f21-a41a-773c91ec9a7e" />


**Question 4**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

```
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```
SELECT
  MAX(purch_amt) AS MAXIMUM
FROM
  orders;

```sql

```

**Output:**

<img width="408" height="298" alt="image" src="https://github.com/user-attachments/assets/10107835-f037-4527-b5d1-1a56814cae17" />


**Question 5**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee
```
name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```
```sql
SELECT
  SUM(income) AS total_income
FROM
  employee
WHERE
  age >= 40;

```

**Output:**

<img width="442" height="308" alt="image" src="https://github.com/user-attachments/assets/2cc068bf-0415-4b4c-937a-d3baf1cb7fba" />

**Question 6**
---
Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee

```sql
SELECT
  COUNT(*) AS COUNT
FROM
  employee
WHERE
  age > 32;
```

**Output:**

<img width="439" height="321" alt="image" src="https://github.com/user-attachments/assets/f8ab4912-9f63-4ef1-b23f-c1126340c669" />


**Question 7**
---
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer
```
name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```

```sql
SELECT
  AVG(LENGTH(name)) AS avg_name_length
FROM
  customer
WHERE
  city = 'Chennai';
```

**Output:**

<img width="445" height="296" alt="image" src="https://github.com/user-attachments/assets/88ea5411-f1c9-4bbb-9d7a-7aff99123a61" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1

```
jdate       MAX(workhour)
----------  -------------
2004.0      15
2006.0      15
```

```sql
SELECT
  jdate,
  MAX(workhour) AS "MAX(workhour)"
FROM
  employee1
GROUP BY
  jdate
HAVING
  MAX(workhour) > 12;
```

**Output:**

<img width="673" height="376" alt="image" src="https://github.com/user-attachments/assets/64b970be-9ceb-4e3a-bb5f-d5ddc2c0b4b1" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1

```
occupation  SUM(workhour)
----------  -------------
Business    30
Doctor      30
Engineer    24
Teacher     27
```

```sql
SELECT
  occupation,
  SUM(workhour) AS "SUM(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  SUM(workhour) > 20;
```

**Output:**

<img width="619" height="432" alt="image" src="https://github.com/user-attachments/assets/ddf4d318-df1b-4afd-938e-1de95874999a" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

```
occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0
```

```sql
SELECT
  occupation,
  AVG(workhour) AS "AVG(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="757" height="392" alt="image" src="https://github.com/user-attachments/assets/44ae7e60-e769-4e14-88cd-50a46831418f" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
