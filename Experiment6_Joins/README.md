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
<img width="1276" height="515" alt="Screenshot 2026-08-31 105543" src="https://github.com/user-attachments/assets/2f4eca63-2455-4e5b-b10d-756f17abfdfd" />


```sql
select p.*
from patients p
inner join appointments a
on p.patient_id=a.patient_id
where a.appointment_date between
'2024-02-01' and '2024-02-28';
```

**Output:**

<img width="1295" height="435" alt="Screenshot 2026-08-31 105557" src="https://github.com/user-attachments/assets/47ae3eeb-fba3-4949-81b6-4cbd9af7fac7" />


**Question 2**
---
<img width="1290" height="498" alt="Screenshot 2026-08-31 105653" src="https://github.com/user-attachments/assets/1b616a79-0cda-42c0-bf6a-d9cc6d58187f" />


```sql
select p.*
from patients p
inner join test_results t
on p.patient_id=t.patient_id
where t.test_name='X-Ray'
and t.result='Normal';
```

**Output:**

<img width="1306" height="430" alt="Screenshot 2026-08-31 105715" src="https://github.com/user-attachments/assets/3c502ee6-4055-45ea-8cf9-2310860f4a97" />


**Question 3**
---
<img width="1283" height="630" alt="Screenshot 2026-08-31 105845" src="https://github.com/user-attachments/assets/13c34497-7ab4-432c-bef2-596fa14fde10" />


```sql
select c.*
from customer c
left join orders o ON c.customer_id=o.customer_id
where o.ord_date>'2012-08-17';
```

**Output:**

<img width="1316" height="788" alt="Screenshot 2026-08-31 105859" src="https://github.com/user-attachments/assets/82bf4223-dbb1-468f-baea-048fc0e91519" />


**Question 4**
---
<img width="1285" height="511" alt="Screenshot 2026-08-31 105949" src="https://github.com/user-attachments/assets/6932a9f5-00c1-4551-a765-2485ae571372" />


```sql
select p.first_name as patient_name,t.*
from patients p
inner join test_results t
on p.patient_id=t.patient_id
where p.admission_date>='2024-01-01'
and p.admission_date<'2024-02-01';
```

**Output:**

<img width="1335" height="447" alt="Screenshot 2026-08-31 105959" src="https://github.com/user-attachments/assets/430b3df1-f9ef-47ff-9d3d-e359d96046c5" />


**Question 5**
---
<img width="1275" height="515" alt="Screenshot 2026-08-31 110054" src="https://github.com/user-attachments/assets/1ad74f72-d754-401c-a4af-73411455976c" />


```sql
select p.*
from patients p
inner join appointments a
on p.patient_id=a.patient_id
where a.appointment_date>='2024-01-01'
and a.appointment_date<'2024-02-01';
```

**Output:**

<img width="1293" height="421" alt="Screenshot 2026-08-31 110105" src="https://github.com/user-attachments/assets/6cc8ad2b-7d51-42d8-b826-95d8c0f375d2" />


**Question 6**
---
<img width="1257" height="526" alt="Screenshot 2026-08-31 110156" src="https://github.com/user-attachments/assets/b623c77b-7f29-4356-a701-7a9c368461f2" />


```sql
select p.first_name as patient_name,d.first_name as doctor_name
from patients p
inner join doctors d
on p.doctor_id=d.doctor_id
where p.discharge_date is NULL;
```

**Output:**

<img width="825" height="478" alt="Screenshot 2026-08-31 110203" src="https://github.com/user-attachments/assets/8bd17f10-7484-49fc-af53-0556c356b383" />


**Question 7**
---
<img width="1287" height="626" alt="Screenshot 2026-08-31 110258" src="https://github.com/user-attachments/assets/a8b10258-daf9-4ced-ae61-468848aaf16b" />


```sql
select p.*
from patients p
inner join doctors d
on p.doctor_id=d.doctor_id
where d.first_name='John'
and d.last_name='Smith';
```

**Output:**

<img width="1357" height="436" alt="Screenshot 2026-08-31 110308" src="https://github.com/user-attachments/assets/bbd40d2d-146c-4a1c-a8f6-82595a5d91ac" />


**Question 8**
---
<img width="1267" height="537" alt="Screenshot 2026-08-31 110343" src="https://github.com/user-attachments/assets/0ea63a6d-2d98-4c67-a96f-5d3f21327f50" />


```sql
select c.*
from customer c
left join salesman s
on c.salesman_id=s.salesman_id
where s.name='Mc Lyon';
```

**Output:**
<img width="1298" height="427" alt="Screenshot 2026-08-31 110353" src="https://github.com/user-attachments/assets/c01d01c9-6d5e-412b-b924-db198a080a59" />


**Question 9**
---
-- Paste Question 9 here<img width="1308" height="602" alt="Screenshot 2026-08-31 110440" src="https://github.com/user-attachments/assets/6357c626-5be4-4f75-9d99-0a50d728e1ec" />

```sql
select c.cust_name,s.name
from customer c
left join salesman s
on c.salesman_id=s.salesman_id
where c.city=s.city;
```

**Output:**

<img width="725" height="507" alt="Screenshot 2026-08-31 110448" src="https://github.com/user-attachments/assets/651e6476-cee0-4ec3-a675-f01f2f28ac4e" />


**Question 10**
---
<img width="1295" height="525" alt="Screenshot 2026-08-31 110533" src="https://github.com/user-attachments/assets/8d5e5c0e-38e1-4247-a7c9-c0e2fc1c0500" />


```sql
select c.*
from customer c
left join orders o
on c.customer_id = o.customer_id
where o.ord_date between '2012-07-01' and '2012-07-30';
```

**Output:**

<img width="1348" height="446" alt="Screenshot 2026-08-31 110541" src="https://github.com/user-attachments/assets/dcc07605-b3b1-402a-836e-69801c5e1791" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
