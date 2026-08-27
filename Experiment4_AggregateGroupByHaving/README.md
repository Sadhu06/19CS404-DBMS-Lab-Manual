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

What is the average duration of insurance coverage for patients covered by each insurance company?

```
SELECT
   InsuranceCompany,
   AVG(
        CAST(strftime('%Y', EndDate) AS INTEGER) - CAST(strftime('%Y', StartDate) AS INTEGER) 
    ) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

<img width="1067" height="776" alt="image" src="https://github.com/user-attachments/assets/2109f51e-5e4c-4742-bb62-be0c0dfc15d6" />


**Question 2**

What is the count of male and female patients?

```
SELECT Gender, COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Gender;
```

**Output:**

<img width="685" height="442" alt="image" src="https://github.com/user-attachments/assets/7e4685c8-a06a-4132-80ac-f0043cdad155" />


**Question 3**

Write a SQL Query to find how many medications are prescribed for each patient?

```
SELECT PatientID, COUNT(Medications) AS AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

<img width="777" height="698" alt="image" src="https://github.com/user-attachments/assets/aa3a6dd2-2482-48f5-8072-3d4fdfed7cbf" />


**Question 4**

Write a SQL query to find  how many employees work in California?

```
SELECT COUNT(*) AS employees_in_california
FROM employee
WHERE city = 'California';
```

**Output:**

<img width="643" height="401" alt="image" src="https://github.com/user-attachments/assets/a52b1ba4-7592-4db8-830e-618d89005a87" />


**Question 5**

Write a SQL query to find the maximum purchase amount.

```
SELECT MAX(purch_amt) AS MAXIMUM
FROM orders;
```

**Output:**

<img width="476" height="387" alt="image" src="https://github.com/user-attachments/assets/b8b49a12-4bac-475d-bda0-4a60cd93888b" />


**Question 6**

Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

```
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="458" height="401" alt="image" src="https://github.com/user-attachments/assets/1b0744a7-6eb3-42ba-afc2-a0ee80857024" />


**Question 7**

Write a SQL query to find the minimum purchase amount.

```
SELECT MIN(purch_amt) AS MINIMUM
FROM orders;
```

**Output:**

<img width="438" height="396" alt="image" src="https://github.com/user-attachments/assets/3e59eff8-55a8-441b-a910-5af51ef34f59" />


**Question 8**

Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

```
SELECT age, SUM(income)
FROM employee
GROUP BY age
HAVING SUM(income) > 1000000;
```

**Output:**

<img width="693" height="493" alt="image" src="https://github.com/user-attachments/assets/c41e4c83-9851-491f-92a3-fd39318e8d12" />


**Question 9**

Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

```
SELECT age, AVG(income)
FROM employee
GROUP BY age
HAVING AVG(income) BETWEEN 300000 AND 500000;
```

**Output:**

<img width="657" height="427" alt="image" src="https://github.com/user-attachments/assets/d437857f-0d90-4204-bcac-7c484d1171a0" />


**Question 10**

Write the SQL query to find how many patients have more than 3 medical records?.

```
SELECT PatientID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID
HAVING COUNT(*) > 3;
```

**Output:**

<img width="691" height="422" alt="image" src="https://github.com/user-attachments/assets/19836260-0a34-47ce-bbea-25986753cb15" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
