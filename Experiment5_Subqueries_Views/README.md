# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

![WhatsApp Image 2025-04-30 at 17 37 35_34b13d27](https://github.com/user-attachments/assets/2c0cd8ed-ab19-4d21-aff8-b3f041699ebc)


```sql
SELECT medication_id as medic,medication_name,dosage
FROM Medications
WHERE dosage = (SELECT MIN(dosage) FROM Medications);
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 38 19_fe7a24c2](https://github.com/user-attachments/assets/85ed8ba0-f6eb-4969-84b1-7e07aa3c9f9c)

**Question 2**
---
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

![WhatsApp Image 2025-04-30 at 17 38 56_490cb70e](https://github.com/user-attachments/assets/9d7bad80-9141-496a-a9e7-786c28be1322)

```sql
SELECT * FROM GRADES g
WHERE grade = (SELECT MIN(grade) FROM GRADES
WHERE subject = g.subject);
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 39 50_59f05199](https://github.com/user-attachments/assets/5f0a6ee9-d25f-4205-b50a-e6178fff18e3)


**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

![WhatsApp Image 2025-04-30 at 17 40 31_75777eb1](https://github.com/user-attachments/assets/41cef261-c1b1-4719-8a47-7f6a4fb1f5ad)

```sql
SELECT * FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 41 14_297d57f2](https://github.com/user-attachments/assets/28ebf385-8d8f-4806-b818-42d79f759514)


**Question 4**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

![WhatsApp Image 2025-04-30 at 17 42 04_6a6d6f08](https://github.com/user-attachments/assets/f5cf7d7b-f9d3-43f3-b7f4-8d0c2d811cfd)


```sql
SELECT id,name,age,city,income
FROM Employee
WHERE age < (SELECT AVG(age) FROM Employee
WHERE income > 250000);
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 43 11_325f3c9b](https://github.com/user-attachments/assets/e32b9680-42cd-4984-89af-9952baa2c8fa)


**Question 5**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

![WhatsApp Image 2025-04-30 at 17 44 03_30375ec8](https://github.com/user-attachments/assets/4b3124c2-8861-4689-b53f-5e96b937bcba)

```sql
SELECT s.salesman_id,s.name
FROM salesman s
JOIN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
) c ON s.salesman_id = c.salesman_id;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 44 54_07627dd0](https://github.com/user-attachments/assets/87ecc91d-97ec-4a42-963a-be55b18f685c)

**Question 6**
---
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

![WhatsApp Image 2025-04-30 at 17 46 03_e4198f8f](https://github.com/user-attachments/assets/8c940491-44a5-4359-952d-be7663a60f37)


```sql
SELECT medication_id as medic,medication_name,dosage
FROM Medications
WHERE dosage = (SELECT MAX(dosage) FROM Medications);
```

**Output:**

![image](https://github.com/user-attachments/assets/d5c346ad-f51a-4272-b30e-a46b9bd02884)


**Question 7**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

![WhatsApp Image 2025-04-30 at 17 48 14_8d62ea07](https://github.com/user-attachments/assets/dd1106b7-3268-47d5-8fb0-7290487ae17c)

```sql
SELECT * FROM CUSTOMERS
WHERE SALARY < 2500;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 48 53_0ef94724](https://github.com/user-attachments/assets/1cd0813f-e14a-4cf5-afbd-3063f8d9bf97)

**Question 8**
---
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

![WhatsApp Image 2025-04-30 at 17 49 31_0089e124](https://github.com/user-attachments/assets/83ffd277-2ea8-49a7-bfa3-70ec9e483b0e)


```sql
SELECT * FROM GRADES g
WHERE grade=(SELECT MAX(grade) FROM GRADES
WHERE subject = g.subject);
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 50 07_71054bbe](https://github.com/user-attachments/assets/880cb0d0-66c2-4d7e-91f2-60d05b60b20c)


**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS

![WhatsApp Image 2025-04-30 at 17 50 48_19da913c](https://github.com/user-attachments/assets/a3a289c4-7f40-4eab-a9a7-68cf6b35c947)

```sql
SELECT * FROM CUSTOMERS
WHERE SALARY>4500;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 51 27_ff2e37e2](https://github.com/user-attachments/assets/ba333a9c-4209-4198-9ae5-707b11a8ba23)


**Question 10**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

![WhatsApp Image 2025-04-30 at 17 51 58_ba6da75b](https://github.com/user-attachments/assets/7f5cb84c-53ac-4a1d-ae26-af51e6b45f53)

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);

```

**Output:**

![image](https://github.com/user-attachments/assets/c63d8b67-b074-42b5-bc47-cd43e1b59b95)

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
