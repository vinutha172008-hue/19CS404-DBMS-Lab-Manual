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
<img width="1233" height="388" alt="Screenshot 2026-08-21 124423" src="https://github.com/user-attachments/assets/96e25a02-f768-4378-b5ad-6d700ec087cb" />


```sql
DELETE FROM customer
WHERE CUST_CITY!= 'New York'
AND OUTSTANDING_AMT>5000;
```

**Output:**

<img width="1388" height="355" alt="Screenshot 2026-08-21 124442" src="https://github.com/user-attachments/assets/60ea8ff6-ffec-442a-88e0-0e12003bc24d" />


**Question 2**
---
<img width="759" height="171" alt="Screenshot 2026-08-21 130046" src="https://github.com/user-attachments/assets/8cefb6e0-0b9e-47fc-8097-ce75e843172b" />


```sql
UPDATE products
SET product_name='Grapefruit'
WHERE product_id=4;
```

**Output:**

<img width="1126" height="251" alt="Screenshot 2026-08-21 130059" src="https://github.com/user-attachments/assets/b451adcd-22dc-45a2-a685-4cc2c34a9b20" />


**Question 3**
---
<img width="752" height="372" alt="Screenshot 2026-08-21 130150" src="https://github.com/user-attachments/assets/1c997885-a41b-414d-9421-aa6e1c671842" />


```sql
SELECT *
FROM EmployeePosition
ORDER BY Salary DESC
LIMIT 3;
```

**Output:**

<img width="1032" height="309" alt="Screenshot 2026-08-21 130159" src="https://github.com/user-attachments/assets/0fd56d03-4f2f-4a60-80e4-a15e5d26da16" />


**Question 4**
---
<img width="769" height="419" alt="Screenshot 2026-08-21 130254" src="https://github.com/user-attachments/assets/956fc7a0-a920-4ceb-b48d-998d4985cb8d" />


```sql
UPDATE products
SET reorder_lvl=40
WHERE category='Grocery';
```

**Output:**

<img width="1311" height="403" alt="Screenshot 2026-08-21 130313" src="https://github.com/user-attachments/assets/e6019ef8-034b-4e16-82e2-2342d52a1ebb" />


**Question 5**
---
<img width="1225" height="413" alt="Screenshot 2026-08-21 130602" src="https://github.com/user-attachments/assets/c25e9e41-e0b2-4cb5-ae7a-b3bd71220881" />


```sql
DELETE FROM customer
WHERE CUST_NAME LIKE '%Holmes%';
```

**Output:**

<img width="1326" height="496" alt="Screenshot 2026-08-21 130634" src="https://github.com/user-attachments/assets/997172a9-9355-437d-a9b9-2d14b94b3517" />


**Question 6**
---
<img width="1243" height="455" alt="Screenshot 2026-08-21 130906" src="https://github.com/user-attachments/assets/2e73579f-db7f-4b71-acae-9a353fe3d170" />


```sql
SELECT product_id, original_price, discount_percentage, (original_price*(1-discount_percentage)) AS discounted_price
FROM Products
WHERE original_price BETWEEN 50 AND 150;
```

**Output:**

<img width="1204" height="280" alt="Screenshot 2026-08-21 130914" src="https://github.com/user-attachments/assets/a790f657-889c-42a4-9a2f-cf7f6933cfbe" />


**Question 7**
---
<img width="807" height="404" alt="Screenshot 2026-08-21 131005" src="https://github.com/user-attachments/assets/ab63f2e0-45b5-4093-a8a5-db96e2ded7d7" />


```sql
SELECT UPPER(EmpFname) AS EmpName
FROM EmployeeInfo;
```

**Output:**

<img width="478" height="316" alt="Screenshot 2026-08-21 131011" src="https://github.com/user-attachments/assets/140b6b3f-0e42-4e4a-b0a2-7b762894e7d4" />


**Question 8**
---
<img width="854" height="259" alt="Screenshot 2026-08-21 131131" src="https://github.com/user-attachments/assets/5c2df3c0-ddd0-44a6-8b87-35bec33c0506" />


```sql
UPDATE suppliers
SET supplier_name='A1 Suppliers'
WHERE supplier_id=8;
```

**Output:**
<img width="1365" height="418" alt="Screenshot 2026-08-21 131145" src="https://github.com/user-attachments/assets/e2182905-0d9d-4480-b0cc-7d9fdd98f169" />


**Question 9**
---

<img width="677" height="526" alt="Screenshot 2026-08-21 131310" src="https://github.com/user-attachments/assets/dcd7a90b-cb54-47cf-bf36-497b6d15a745" />


```sql
SELECT ename, hiredate, date(hiredate, '+100 days') AS DateAfter100Days
FROM emp;
```

**Output:**


<img width="779" height="386" alt="Screenshot 2026-08-21 131317" src="https://github.com/user-attachments/assets/24182635-bb8c-4e41-92a4-d0b188c7d62a" />


**Question 10**
---

<img width="772" height="461" alt="Screenshot 2026-08-21 131325" src="https://github.com/user-attachments/assets/a2c1df6a-1147-413e-956a-0c6233e08547" />


```sql
SELECT id, value1, ABS(value1) AS absolute_value
FROM calculations;
```

**Output:**


<img width="755" height="320" alt="Screenshot 2026-08-21 131333" src="https://github.com/user-attachments/assets/4128568b-3ce0-462e-86c3-32f016cbd39c" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
