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
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients AS p
INNER JOIN 
    test_results AS t
ON 
    p.patient_id = t.patient_id
WHERE 
    t.test_name = 'Blood Pressure';
```

**Output:**

<img width="1287" height="419" alt="image" src="https://github.com/user-attachments/assets/fd4800cf-a43c-458b-8d90-39d693ad1120" />

**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.

```sql
SELECT 
    n.*
FROM 
    nurses AS n
INNER JOIN 
    departments AS d
ON 
    n.department_id = d.department_id
WHERE 
    d.department_name = 'Pediatrics';

```

**Output:**

<img width="1277" height="420" alt="image" src="https://github.com/user-attachments/assets/81a5d322-2b21-4938-8b75-249fcaa2b59b" />

**Question 3**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM 
    customer AS c
INNER JOIN 
    salesman AS s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="1283" height="792" alt="image" src="https://github.com/user-attachments/assets/99f437eb-705c-45b3-a0da-e15637d87aa6" />

**Question 4**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer AS c
INNER JOIN 
    salesman AS s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**

<img width="1283" height="786" alt="image" src="https://github.com/user-attachments/assets/cf5fb88c-5e87-48ee-972c-8c3f0d99df6a" />

**Question 5**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.
```sql
SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer AS c
LEFT JOIN 
    orders AS o
ON 
    c.customer_id = o.customer_id;

```

**Output:**

<img width="1203" height="983" alt="image" src="https://github.com/user-attachments/assets/eba92a58-a0d9-4fe5-b3fc-3d9c3479f04b" />


**Question 6**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column.
```sql
SELECT 
    s.name,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c
ON 
    s.salesman_id = c.salesman_id;


```

**Output:**

<img width="1284" height="934" alt="image" src="https://github.com/user-attachments/assets/c7c8c8e5-02de-4d78-94ea-02d56f68cd0d" />

**Question 7**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```sql
SELECT 
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM 
    patients AS p
INNER JOIN 
    doctors AS d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="902" height="402" alt="image" src="https://github.com/user-attachments/assets/1e9c26da-848a-41c0-a6da-8f33d4a19e19" />

**Question 8**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer AS c
INNER JOIN 
    salesman AS s
ON 
    c.salesman_id = s.salesman_id;

```

**Output:**

<img width="1285" height="937" alt="image" src="https://github.com/user-attachments/assets/906eb3af-04f5-4dba-afe8-575acff9e10f" />

**Question 9**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

```sql
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman AS s
INNER JOIN 
    customer AS c
ON 
    s.city = c.city;
```

**Output:**

<img width="1192" height="698" alt="image" src="https://github.com/user-attachments/assets/a21b63e5-bfb3-47b0-a053-a55b3219a96e" />


**Question 10**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

```sql
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM 
    customer AS c
INNER JOIN 
    salesman AS s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

<img width="1294" height="928" alt="image" src="https://github.com/user-attachments/assets/948caf29-800d-45f8-951f-9abff0c15b34" />

**Completion Satatus:**

<img width="617" height="165" alt="image" src="https://github.com/user-attachments/assets/50e2b56c-4cd6-442f-8da3-879ed0669c20" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
