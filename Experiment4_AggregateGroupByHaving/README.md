# Experiment 4: Aggregate Functions, Group By and Having Clause
## NAME: HARSHANA M V
## REGISTER NUMBER: 212224240053
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
How many appointments are scheduled for each doctor?

```
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**

<img width="715" height="614" alt="506091703-e7d213cb-9996-46c7-ac2f-e1772a81947c" src="https://github.com/user-attachments/assets/7c7e08cc-609f-4911-89cd-e42cb1956195" />

**Question 2**
---
What is the average dosage prescribed for each medication?

```
SELECT Medication,AVG(Dosage) AS AvgDosage
FROM Prescriptions
GROUP BY Medication
ORDER BY Medication;
```

**Output:**

<img width="615" height="726" alt="506091771-84214c6d-4cc8-422d-a1a0-912ff910bdc4" src="https://github.com/user-attachments/assets/b25e400f-552e-42c3-9522-c24a90cb09b6" />


**Question 3**
---
How many patients are there in each city?
```
SELECT Address,COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Address
ORDER BY Address;
```

**Output:**

<img width="615" height="391" alt="506091835-1ab21e28-2210-4435-a388-a2ef6c172711" src="https://github.com/user-attachments/assets/2de82d49-9bc9-4a5d-9f25-6a4dcc48403e" />


**Question 4**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

```
SELECT COUNT(*) AS COUNT FROM customer
WHERE city!='Noida';
```

**Output:**

<img width="325" height="271" alt="506091898-df40d8e9-9467-49e5-ab6e-9de9c1bd9e87" src="https://github.com/user-attachments/assets/d3726e8f-08ee-4241-8af2-26be216f7c5b" />

**Question 5**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

```
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="343" height="298" alt="506091970-bf6c3561-fd43-43e5-925f-24b328eea611" src="https://github.com/user-attachments/assets/ed0e2889-db8b-4f54-9c3e-72b120f1f296" />


**Question 6**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id

-------------+----------------+------------+-------+-------------

    3002 | Nick Rimando   | New York   |   100 |        5001

    3007 | Brad Davis     | New York   |   200 |        5001

    3005 | Graham Zusi    | California |   200 |        5002

```
SELECT COUNT(*) AS COUNT FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

<img width="327" height="289" alt="506092020-3928cf5a-4add-43c2-9c11-10b7fdbf8a0d" src="https://github.com/user-attachments/assets/972bb5a8-4177-4ddb-ac26-bc94073b60ad" />


**Question 7**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name type

id INTEGER name TEXT age INTEGER city TEXT income INTEGER
```
SELECT COUNT(*) AS employees_count FROM employee
WHERE income>50000;
```

**Output:**

<img width="417" height="299" alt="506092053-14c00730-dd12-4474-8ca4-bda74a98d579" src="https://github.com/user-attachments/assets/da4facb8-1dc7-4409-b9b6-85b704acd9d6" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

```
SELECT (age/5)*5 AS age_group,SUM(salary)
FROM customer1
GROUP BY age_group
HAVING SUM(salary)>5000;
```

**Output:**

<img width="584" height="337" alt="506092118-71bc3589-f2e2-4bfc-844c-b8af0614ce21" src="https://github.com/user-attachments/assets/59409b83-52c6-4efc-9000-dd3d5bd5496a" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

```
SELECT city,AVG(income)
FROM employee
GROUP BY city
HAVING AVG(income)>500000;
```

**Output:**

<img width="573" height="406" alt="506092156-808fd86f-8fe0-486b-8ac8-a4d2699d7305" src="https://github.com/user-attachments/assets/5587ac7d-d672-4383-9ae0-2eafbaa5193f" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

```
SELECT occupation,AVG(workhour)
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="621" height="367" alt="506092209-74a16d49-12d0-4f77-8ef6-e8e6caa28702" src="https://github.com/user-attachments/assets/31aa6a0e-fdbe-4074-903d-191d211df97f" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
