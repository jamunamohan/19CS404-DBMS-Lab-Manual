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
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission.


```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
INNER JOIN 
    customer c ON o.customer_id = c.customer_id
INNER JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/aa9b89d8-64fa-4693-811a-d57f6b94829f)

**Question 2**
---
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.

Sample table: customer



```sql
select c.cust_name as "Customer Name", c.city, s.name as "Salesman" , s.commission
from customer c
inner join salesman s
on c.salesman_id = s.salesman_id
where s.commission > 0.12;
```

**Output:**

![WhatsApp Image 2025-04-30 at 18 05 36_9200de15](https://github.com/user-attachments/assets/902bd9a3-317d-42fb-a4cb-aaa4d6b6e93a)


**Question 3**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

```sql
select s.name as Salesman, c.cust_name, s.city
from salesman s
inner join customer c
on c.city = s.city;
```

**Output:**

![WhatsApp Image 2025-04-30 at 18 08 13_08241303](https://github.com/user-attachments/assets/e814026c-beaf-4182-84f2-1d2a5e4dd159)

**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

![WhatsApp Image 2025-04-30 at 18 09 05_4252aab6](https://github.com/user-attachments/assets/2ddd2a2e-70e0-4c9c-b8f3-64692446fe29)


```sql
select p.first_name as patient_name, t.test_name
from PATIENTS p
inner join test_results t
on p.patient_id = t.patient_id;

```
**Output:**

![WhatsApp Image 2025-04-30 at 18 10 12_ee448b70](https://github.com/user-attachments/assets/50b6e2ce-0fd4-4b2c-ae7c-cce84df16fad)


**Question 5**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for customers with a grade less than or equal to 100.

![WhatsApp Image 2025-04-30 at 18 10 57_ab8d29aa](https://github.com/user-attachments/assets/082bb09b-07ce-4f82-a3ab-5beeab940c63)


```sql
select s.name, c.cust_name , c.city, c.grade, c.salesman_id
from customer c
left join salesman s
on c.salesman_id = s.salesman_id
where c.grade <= 100;
```

**Output:**

![image](https://github.com/user-attachments/assets/41650755-f327-4de5-8fa2-f39fcb585e2d)

**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.

PATIENTS TABLE:

![WhatsApp Image 2025-04-30 at 18 11 54_94dc534c](https://github.com/user-attachments/assets/2760b35b-e0b5-4cbf-9003-503114d6abc2)


```sql
select p.*, d.specialization as doctor_specialization
from patients p
inner join doctors d
on p.doctor_id = d.doctor_id;
```

**Output:**

![WhatsApp Image 2025-04-30 at 18 12 46_70f276a4](https://github.com/user-attachments/assets/435f866c-9f9f-4efb-9f73-ee2dfc8edce4)

**Question 7**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.

![WhatsApp Image 2025-04-30 at 18 13 56_779ea92e](https://github.com/user-attachments/assets/e9aec8d9-e82a-49a3-bfef-2cfef9be6f0f)


```sql
select c.cust_name,o.ord_no,o.ord_date,o.purch_amt
from customer c
left join orders o
on c.customer_id = o.customer_id
where o.purch_amt >1000;
```

**Output:**

![WhatsApp Image 2025-04-30 at 18 15 19_cdabefe9](https://github.com/user-attachments/assets/579d2c86-4799-44ad-9530-e2aa92f5c5c3)


**Question 8**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name,
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON o.salesman_id = s.salesman_id;


```

**Output:**

![WhatsApp Image 2025-04-30 at 18 15 19_cdabefe9](https://github.com/user-attachments/assets/17beebb5-0cfb-4cc9-bff8-2d934cd9e87f)


**Question 9**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

![WhatsApp Image 2025-04-30 at 18 17 19_265d5167](https://github.com/user-attachments/assets/6a36f7cf-789e-4c1f-9a3c-a30fcf2aaeea)


```sql
select p.first_name as patient_name 
from patients p
inner join test_results t
on p.patient_id = t.patient_id
where t.test_name = 'Blood Pressure';

```

**Output:**

![WhatsApp Image 2025-04-30 at 18 18 01_e607ca73](https://github.com/user-attachments/assets/697416d8-73e5-4c01-84e2-7012381d7fb5)


**Question 10**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id.

![WhatsApp Image 2025-04-30 at 18 19 26_8b0b4ca9](https://github.com/user-attachments/assets/5b9b8498-36ae-4f15-92f1-e56d860ffade)


```sql
select c.cust_name, c.city, c.grade, s.name as Salesman, s.city
from customer c
inner join salesman s
on c.salesman_id = s.salesman_id
where c.grade<300
order by customer_id asc;
```

**Output:**

![WhatsApp Image 2025-04-30 at 18 20 25_41114f63](https://github.com/user-attachments/assets/a6f9ff70-6bf5-4a0f-b218-b9da3601e7d0)

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
