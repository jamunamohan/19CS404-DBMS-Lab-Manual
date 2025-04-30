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
How many medical records are there for each patient?

Sample table:MedicalRecords Table

![WhatsApp Image 2025-04-30 at 17 19 36_e70b9cad](https://github.com/user-attachments/assets/ec0fd5a1-dd21-49c7-ade0-a2625451b6b2)

```sql
SELECT PatientID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 20 22_96fdeab4](https://github.com/user-attachments/assets/784d625c-a5c7-4717-a84a-645cdb209777)


**Question 2**
---
How many patients are covered by each insurance company?

Sample table:Insurance Table

![WhatsApp Image 2025-04-30 at 17 21 15_f88dd299](https://github.com/user-attachments/assets/b66c0bc6-d8b4-4fbe-a98f-58114b02510c)


```sql
SELECT InsuranceCompany,COUNT(*) AS TotalPatients
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 22 16_b475f09a](https://github.com/user-attachments/assets/8f231084-e886-4724-88d1-4ea6874582ec)


**Question 3**
---
What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table

![WhatsApp Image 2025-04-30 at 17 23 07_30249397](https://github.com/user-attachments/assets/b0ba78c7-0fcc-4c22-8f2e-5114675f835b)


```sql
SELECT Medication,AVG(Dosage) AS AvgDosage
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 24 02_ef80b554](https://github.com/user-attachments/assets/10664ba9-2e8e-41e2-a17c-cf2def9ba213)


**Question 4**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

![WhatsApp Image 2025-04-30 at 17 25 26_c23bff49](https://github.com/user-attachments/assets/2c157a9b-b4eb-41b4-ae41-da1c82ede4c4)


```sql
SELECT MAX(purch_amt) AS MAXIMUM
FROM orders
LIMIT 1;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 26 03_f16e6766](https://github.com/user-attachments/assets/a0e6a254-523a-4123-bf91-5dc7453f3c78)


**Question 5**
---
Write a SQL query to find the average salary of all employees?

Table: employee

![WhatsApp Image 2025-04-30 at 17 26 40_bced677d](https://github.com/user-attachments/assets/a380c1a7-d5eb-4e37-8816-8c3b76ad34ed)


```sql
SELECT avg(income) AS Average_Salary
FROM employee
LIMIT 1;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 27 15_4223c386](https://github.com/user-attachments/assets/f573d42d-9f5b-4b2e-bdfa-60dde86ef42a)


**Question 6**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

![WhatsApp Image 2025-04-30 at 17 27 52_f4fc64cc](https://github.com/user-attachments/assets/3a53e42d-0bb0-4252-b270-b34608f32cd0)


```sql
SELECT COUNT(*) AS COUNT
FROM customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/8acdce76-8897-4863-b544-77287ef88fb5)


**Question 7**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

![WhatsApp Image 2025-04-30 at 17 28 55_9a879401](https://github.com/user-attachments/assets/e21eea7b-b178-41a9-ab3b-74616c4b5024)

```sql
SELECT SUM(income) as total_income
FROM employee
WHERE age >= 40
LIMIT 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/20665487-3132-4153-81cf-5dd1c912330a)

**Question 8**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1

![WhatsApp Image 2025-04-30 at 17 29 59_7a8a48e3](https://github.com/user-attachments/assets/e385412c-2b91-460c-8210-af973f2ecb35)

```sql
SELECT occupation,MIN(workhour)
FROM employee1
GROUP BY occupation
HAVING MIN(workhour) > 8
ORDER BY occupation;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 30 34_8d89ecfb](https://github.com/user-attachments/assets/43a8b861-911b-4597-8a8b-9d6b9291fd36)


**Question 9**
---
Write the SQL query that performs grouping by age groups and displays the maximum salary for each group, excluding groups where the maximum salary is not greater than 8000.

Note: Calculate the age group as multiples of 5.

Eg., 20,22,23 comes in age group 20.

25,27,29 comes in age group 25.

Sample table: customer1

![WhatsApp Image 2025-04-30 at 17 31 14_440e80de](https://github.com/user-attachments/assets/d46fde79-2f27-4de8-b77a-1f4f3ddfe0d6)

```sql
SELECT (age-(age % 5)) as age_group,MAX(salary)
FROM customer1
GROUP BY age_group
HAVING MAX(salary) > 8000
ORDER BY age_group;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 31 52_7c6db1ab](https://github.com/user-attachments/assets/9ff4ff95-3ee8-40f0-a64d-d8e904aef346)


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by age intervals using the expression (age/5)5, calculates the minimum age for each group, and excludes groups where the minimum age is not less than 25.

Sample table: customer1

![WhatsApp Image 2025-04-30 at 17 32 28_756e6d65](https://github.com/user-attachments/assets/d437f589-edef-4f46-a772-e91f7a597f78)


```sql
SELECT (age/5)*5 AS age_group,MIN(age)
FROM customer1
GROUP BY age_group
HAVING MIN(age) < 25;

```

**Output:**

![WhatsApp Image 2025-04-30 at 17 33 00_ca57c61f](https://github.com/user-attachments/assets/72ed4a68-722e-4364-b1cd-7753ca080464)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
