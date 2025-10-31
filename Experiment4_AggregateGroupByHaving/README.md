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
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

```sql
select Frequency,COUNT(*) AS TotalPrescriptions
from Prescriptions
GROUP BY Frequency

```

**Output:**

<img width="793" height="532" alt="image" src="https://github.com/user-attachments/assets/1e57713e-58b6-4fd5-907d-bbaef72ea339" />

**Question 2**
---
Write a SQL Query to find how many medications are prescribed for each patient?

```sql
select PatientID,count(Medications) as AvgMedications from MedicalRecords group by PatientID;
```

**Output:**

<img width="688" height="612" alt="image" src="https://github.com/user-attachments/assets/eef05d4f-1830-42a9-8de3-afa116075fbd" />


**Question 3**
---
How many prescriptions were written by each doctor?

```sql
select DoctorID,count(*) as TotalPrescriptions from Prescriptions group by DoctorID;
```

**Output:**

<img width="726" height="755" alt="image" src="https://github.com/user-attachments/assets/b8b84725-b23d-4688-ae05-19ea5cee9841" />


**Question 4**
---
Write a SQL query to find the shortest email address in the customer table?

```sql
select name,
        email,
        length(email) as min_email_length
from 
    customer
order by
    length(email) asc
limit 1;
```

**Output:**

<img width="1023" height="317" alt="image" src="https://github.com/user-attachments/assets/08b7c9db-cd4f-49df-9f12-f3306c2b6eb2" />


**Question 5**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

```sql
select count(*) as COUNT from customer where grade is not null;
```

**Output:**

<img width="425" height="315" alt="image" src="https://github.com/user-attachments/assets/4c51e9a5-70c6-4144-9045-1cbcbf6ac1c3" />


**Question 6**
---
Write a SQL query to find  how many employees work in California?

```sql
SELECT COUNT(*) AS employees_in_california from employee where city='California';
```

**Output:**

<img width="644" height="316" alt="image" src="https://github.com/user-attachments/assets/d091d670-e3fd-45b4-ae60-49a9d07d3efc" />

**Question 7**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

```sql
select avg(income) as avg_income from employee where name like 'A%';```

**Output:**

<img width="405" height="319" alt="image" src="https://github.com/user-attachments/assets/4edd59fd-a6e5-418f-878a-ec61487b1c5d" />

**Question 8**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

```sql
SELECT category_id,
sum(price) as Total_Cost from products
group by category_id
having sum(price)>50;```

**Output:**

<img width="637" height="339" alt="image" src="https://github.com/user-attachments/assets/429b598c-ce59-4753-87c0-8cfd554af94d" />

**Question 9**
---
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

```sql
select address,AVG(salary) from customer1  group by address having avg(salary)<15000;
```

**Output:**

<img width="679" height="607" alt="image" src="https://github.com/user-attachments/assets/f69dbb35-710d-4903-9a43-9ed67411f9e9" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000

```sql
SELECT city,AVG(income)  from employee group by city having AVG(income)>500000;
```

**Output:**

<img width="604" height="437" alt="image" src="https://github.com/user-attachments/assets/5517899a-cd54-4614-81d0-b7a3697f99ec" />
## Completion status:
<img width="623" height="186" alt="image" src="https://github.com/user-attachments/assets/59b1e026-e932-49e7-ba63-99b3c63a3f3b" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
