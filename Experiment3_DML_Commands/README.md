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
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.
![WhatsApp Image 2025-04-30 at 16 52 34_4490838f](https://github.com/user-attachments/assets/aba62e27-cadf-4058-8681-c421e1684a45)

```sql
UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**
![WhatsApp Image 2025-04-30 at 16 53 25_ff350b3c](https://github.com/user-attachments/assets/86ffbb58-f16e-47e9-a161-1f335c3f03a5)

**Question 2**
---
Write a SQL query to Retrieve the department name and location concatenated with a comma.
![WhatsApp Image 2025-04-30 at 16 54 29_bf2fa6a6](https://github.com/user-attachments/assets/328b7ccd-31d9-4623-a9d1-7d49c85e7f49)

```sql
SELECT dname || ', ' || loc AS dept_location
FROM dept;
```

**Output:**
![WhatsApp Image 2025-04-30 at 16 55 12_7bd2417a](https://github.com/user-attachments/assets/a0a0142c-f74e-43b2-87ee-ee911bbaa27f)

**Question 3**
---
Write a SQL query to find the exact date that is 100 days after each employee's hire date.
![WhatsApp Image 2025-04-30 at 16 57 01_8e76dc27](https://github.com/user-attachments/assets/02ee4a98-f413-476d-abba-40777107b491)

```sql
SELECT ename,hiredate,DATE(JULIANDAY(hiredate)+100) AS DateAfter100Days
FROM emp;
```

**Output:**

![WhatsApp Image 2025-04-30 at 16 57 52_d9333b9c](https://github.com/user-attachments/assets/7d37c9cf-8f1c-4aa2-bf22-4c70f63b0a04)

**Question 4**
---
Write a SQL query to calculate the number of days between the hiredate and a specified date ('2024-12-31') for each employee using the JULIANDAY function from the emp table.
![WhatsApp Image 2025-04-30 at 16 58 34_615527a0](https://github.com/user-attachments/assets/9823743b-55fc-46e3-ac45-cdf07d0eefbb)

```sql
SELECT ename,hiredate,JULIANDAY('2024-12-31') - JULIANDAY(hiredate) AS days_worked
FROM emp;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 01 42_e6d9e2dd](https://github.com/user-attachments/assets/ee6206d2-1cd9-44b8-bcd9-78bade14ab6a)


**Question 5**
---
Write a SQL query to calculate the discounted price for products where the discount percentage is greater than 0, and order the results by discounted_price in ascending order. Return product_id, original_price, discount_percentage, and discounted_price.

![WhatsApp Image 2025-04-30 at 17 02 22_abf131ea](https://github.com/user-attachments/assets/7a167e18-ce5a-4f82-b6d0-bf04f72d8298)

```sql
SELECT product_id , original_price ,discount_percentage , (original_price *(1-Discount_percentage)) AS discounted_price
FROM Products
WHERE discount_percentage > 0 
ORDER BY discounted_price ASC;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 03 06_b12dd3e2](https://github.com/user-attachments/assets/96b80ee9-611f-4ac1-b95c-cd26c09c5a56)


**Question 6**
---
Write a SQL query to round the decimal column to 3 decimal places from the Calculations table.
![WhatsApp Image 2025-04-30 at 17 03 50_95745ed2](https://github.com/user-attachments/assets/dca89c6a-ef02-4ecf-837c-c81ea6273de5)

```sql
SELECT id,ROUND(decimal,3) AS rounded_value
FROM Calculations;

```

**Output:**

![image](https://github.com/user-attachments/assets/471e1e67-80a2-47a1-ba41-2ec22fe3fc04)

**Question 7**
---
Write a SQL query to categorize decimal as 'High', 'Medium', or 'Low' based on whether it is greater than 100, between 50 and 100, or less than 50 in the Calculations table
![WhatsApp Image 2025-04-30 at 17 04 57_d888c830](https://github.com/user-attachments/assets/0d3c428b-6bfb-4cc4-9ffa-874ecef99fa8)

```sql
SELECT id, decimal,
CASE
WHEN decimal > 100 THEN 'High'
WHEN decimal BETWEEN 50 AND 100 THEN 'Medium'
ELSE 'Low'
END AS category
FROM Calculations;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 05 41_54873db1](https://github.com/user-attachments/assets/da6b81d7-07c4-41e0-a87e-f747840f2f8c)


**Question 8**
---
Write a SQL query to Select all patients who were admitted for one day.

Table: Patients
![WhatsApp Image 2025-04-30 at 17 06 29_6ebfda5d](https://github.com/user-attachments/assets/b22d8d41-ee05-4696-a66f-1c51a77886e1)

```sql
SELECT patient_id , first_name , admission_date , discharge_date
FROM Patients
WHERE admission_date = discharge_date ;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 07 17_f4cbe546](https://github.com/user-attachments/assets/979c18c4-92d2-49b8-a4b5-dd2413afed0e)


**Question 9**
---
Show the categoryName and description from the categories table sorted by categoryName.
![WhatsApp Image 2025-04-30 at 17 08 31_7fd9f42b](https://github.com/user-attachments/assets/aa72a0c3-1184-4e18-9afe-67dc1e413b02)

```sql
SELECT CategoryName , Description
FROM categories
ORDER BY categoryName ASC;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 09 13_6a09cbb0](https://github.com/user-attachments/assets/34ff532d-0fdc-46cd-b535-6b64bbb10bc4)


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.
```sql
DELETE FROM Customer
WHERE grade <> 3;
```

**Output:**

![WhatsApp Image 2025-04-30 at 17 10 05_d5cbf349](https://github.com/user-attachments/assets/34152a0c-1257-40dc-898a-59b955c83f64)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
