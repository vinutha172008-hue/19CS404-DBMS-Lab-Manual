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
<img width="827" height="561" alt="Screenshot 2026-08-31 103859" src="https://github.com/user-attachments/assets/9d69222a-8f2d-49ac-bd33-7488d149e8d6" />


```sql
select ord_no,purch_amt,ord_date,customer_id,salesman_id
from Orders
where salesman_id IN (
select salesman_id
from Orders
where customer_id=3007
);
```

**Output:**
<img width="867" height="535" alt="Screenshot 2026-08-31 103914" src="https://github.com/user-attachments/assets/24ea4ac4-1535-4de8-8492-7b4543ad33d6" />



**Question 2**
---
<img width="828" height="571" alt="Screenshot 2026-08-31 104043" src="https://github.com/user-attachments/assets/387fbb6d-05d7-4772-83b6-68d737e198ab" />


```sql
select *
from customer
where city <> (
select city
from customer
order by id DESC
limit 1
);
```

**Output:**

<img width="1192" height="500" alt="Screenshot 2026-08-31 104102" src="https://github.com/user-attachments/assets/a2c8b222-a54d-4fd7-9587-e3a9970e835f" />


**Question 3**
---
<img width="1167" height="492" alt="Screenshot 2026-08-31 104331" src="https://github.com/user-attachments/assets/302a354c-6bc8-453b-bb55-a488d3d64613" />


```sql
select ord_no,purch_amt,ord_date,customer_id,salesman_id
from Orders
where salesman_id= (
select salesman_id
from Salesman
where name='Paul Adam'
);
```

**Output:**

<img width="1242" height="390" alt="Screenshot 2026-08-31 104341" src="https://github.com/user-attachments/assets/b5f2eb81-a836-488a-a86d-3bdb4338d1de" />


**Question 4**
---
<img width="1180" height="647" alt="Screenshot 2026-08-31 104432" src="https://github.com/user-attachments/assets/189244c1-17ae-4b5a-86b5-de5057ad4a58" />


```sql
select o.ord_no,purch_amt,o.ord_date,o.customer_id,o.salesman_id
from ORDERS o
join SALESMAN s ON o.salesman_id = s.salesman_id
where s.city='New York';
```

**Output:**

<img width="1148" height="497" alt="Screenshot 2026-08-31 104442" src="https://github.com/user-attachments/assets/9b09d7fe-ce22-4182-ab41-710cc3b923b7" />


**Question 5**
---
<img width="837" height="407" alt="Screenshot 2026-08-31 104539" src="https://github.com/user-attachments/assets/7e2e03c9-37c0-43a7-9c87-9e87cece6021" />


```sql
select medication_id,medication_name,dosage
from Medications
where dosage = (
select MIN(dosage)
from Medications
);
```

**Output:**

<img width="802" height="395" alt="Screenshot 2026-08-31 104546" src="https://github.com/user-attachments/assets/26a2bdfc-14f5-4046-9fe9-2b28dbc0c5f7" />


**Question 6**
---
<img width="972" height="587" alt="Screenshot 2026-08-31 104639" src="https://github.com/user-attachments/assets/900d392a-ab09-4021-be13-477f08feeb30" />


```sql
select s.salesman_id,s.name
from salesman s
join customer c ON s.salesman_id = c.salesman_id
group by s.salesman_id,s.name
having count(c.customer_id)>1;
```

**Output:**

<img width="566" height="457" alt="Screenshot 2026-08-31 104646" src="https://github.com/user-attachments/assets/681be0ea-6ff1-4543-9147-257e403d5db5" />


**Question 7**
---
<img width="853" height="517" alt="Screenshot 2026-08-31 104740" src="https://github.com/user-attachments/assets/2a619861-dabb-44b2-8cc0-afe9779108b3" />


```sql
select *
from CUSTOMERS
where SALARY=1500;
```

**Output:**

<img width="1031" height="382" alt="Screenshot 2026-08-31 104749" src="https://github.com/user-attachments/assets/efe17e36-e860-4fd9-821f-f4b794b8790e" />


**Question 8**
---
<img width="876" height="543" alt="Screenshot 2026-08-31 104848" src="https://github.com/user-attachments/assets/6bc865ed-621e-43cd-afa8-76e8a3523655" />


```sql
select commission
from salesman
where salesman_id IN (
select salesman_id
from customer
where city ='Paris'
);
```

**Output:**

<img width="347" height="341" alt="Screenshot 2026-08-31 104855" src="https://github.com/user-attachments/assets/fd5a7a61-f125-44c6-83f1-882e07804887" />


**Question 9**
---
<img width="898" height="442" alt="Screenshot 2026-08-31 104943" src="https://github.com/user-attachments/assets/6c194e11-78f8-447b-8a85-0dede8a3a4aa" />


```sql
select name,city
from customer
where city IN (
select city
from customer
where id IN (3,7)
);
```

**Output:**

<img width="541" height="445" alt="Screenshot 2026-08-31 104950" src="https://github.com/user-attachments/assets/5a9ebc6c-cb95-426b-baf4-ab3179380f08" />


**Question 10**
---
<img width="1230" height="512" alt="Screenshot 2026-08-31 105039" src="https://github.com/user-attachments/assets/525332de-68ab-4a63-b6a5-a34281bf8002" />


```sql
select ord_no,purch_amt,ord_date,customer_id,salesman_id
from ORDERS
where purch_amt > (
select AVG(purch_amt)
from ORDERS
where ord_date = '2012-10-10'
);
```

**Output:**

<img width="1193" height="470" alt="Screenshot 2026-08-31 105048" src="https://github.com/user-attachments/assets/b08ba079-52dd-45a3-aaa8-466bbaa4cc0f" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
