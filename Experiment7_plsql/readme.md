# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
sql
```
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.
- PL/SQL QUERY
  ~~~
  DECLARE
   a NUMBER := 80;
   b NUMBER := 50;
  BEGIN
   IF a > b THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
   END IF;
  END;
  ~~~

**Expected Output:**  
Greater number is: 80

**Output:**

![WhatsApp Image 2025-05-19 at 12 46 40_32088d69](https://github.com/user-attachments/assets/f6552cd6-2ee7-4b7d-ad51-7c70642a4f47)


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.
  ~~~
  DECLARE
   n     INTEGER := 10; 
   i     INTEGER := 1;   
   sum   INTEGER := 0;  
  BEGIN
   WHILE i <= n LOOP
      sum := sum + i;
      i := i + 1;
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
  END;

**Expected Output:**  
Sum of first 10 natural numbers is: 55

Output:

![image](https://github.com/user-attachments/assets/47b4ed0c-59e1-48f3-a656-a038be366190)


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

Output:

![image](https://github.com/user-attachments/assets/5813cc56-8796-4e9b-9c2b-e28289d0906a)

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.
pql
```
DECLARE
    n NUMBER := 7;           -- Number of terms in the Fibonacci sequence
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 3;
    output VARCHAR2(1000);
BEGIN
    -- Initialize the output with the first two terms
    IF n = 1 THEN
        output := TO_CHAR(a);
    ELSIF n >= 2 THEN
        output := TO_CHAR(a) || ', ' || TO_CHAR(b);
    END IF;

    WHILE i <= n LOOP
        c := a + b;
        output := output || ', ' || TO_CHAR(c);
        a := b;
        b := c;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || output);
END;
```
**Expected Output:**  
n = 1535  
Reversed number is 5351

Output:

![image](https://github.com/user-attachments/assets/9224dbda-f6e7-41a0-82ea-668317c7d742)

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.
- Pql
  ```
  DECLARE
   a INTEGER := 10;
   b INTEGER := 9;
   c INTEGER := 15;
   BEGIN
   IF a >= b AND a >= c THEN
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || a);
   ELSIF b >= a AND b >= c THEN
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || b);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || c);
   END IF;
  END;
  ```
**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

Output:

![image](https://github.com/user-attachments/assets/e9ffee9d-82aa-4449-b721-8f7a2ca28b11)


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
