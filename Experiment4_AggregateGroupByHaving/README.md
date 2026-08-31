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
<img width="780" height="468" alt="Screenshot 2026-08-31 101733" src="https://github.com/user-attachments/assets/cc154d76-6eb0-4e47-b83f-6f4aa473c567" />


```sql
select count(DISTINCT city) as unique_cities
from customer;
```

**Output:**
<img width="578" height="397" alt="Screenshot 2026-08-31 101817" src="https://github.com/user-attachments/assets/954d7d49-338b-450a-8f8e-a55e06ba0284" />


**Question 2**
---
<img width="897" height="720" alt="Screenshot 2026-08-31 101846" src="https://github.com/user-attachments/assets/83facad0-4543-4830-b986-74fbd5aa1bb2" />


```sql
select count(*) as COUNT
from customer
where city <> 'Noida';
```

**Output:**

<img width="521" height="386" alt="Screenshot 2026-08-31 101922" src="https://github.com/user-attachments/assets/9fb3411f-fb6d-485f-885f-07169d16151c" />


**Question 3**
---
<img width="771" height="456" alt="Screenshot 2026-08-31 102011" src="https://github.com/user-attachments/assets/dbdeccf8-0e3c-41ed-803a-fa5990307f78" />


```sql
select count(*) as COUNT
from employee
where age>32;
```

**Output:**

<img width="486" height="392" alt="Screenshot 2026-08-31 102053" src="https://github.com/user-attachments/assets/9db75185-26e8-4c05-b9a2-e5964f8389ff" />


**Question 4**
---
<img width="901" height="418" alt="Screenshot 2026-08-31 102118" src="https://github.com/user-attachments/assets/768ffdc0-fc9d-49a3-b392-8cbb7b0256d0" />


```sql
select Diagnosis, count(*) as DiagnosisCount
from MedicalRecords
group by Diagnosis
order by DiagnosisCount DESC
limit 1;

```

**Output:**

<img width="855" height="387" alt="Screenshot 2026-08-31 102151" src="https://github.com/user-attachments/assets/761c53b0-ed48-4432-a454-8b79c87b1228" />


**Question 5**
---
<img width="902" height="591" alt="Screenshot 2026-08-31 102336" src="https://github.com/user-attachments/assets/6b8b84a0-d973-4c80-b575-99621bf58215" />


```sql
select Frequency,count(PrescriptionID) as TotalPrescriptions
from Prescriptions
group by Frequency;
```

**Output:**

<img width="845" height="620" alt="Screenshot 2026-08-31 102355" src="https://github.com/user-attachments/assets/1995cdbf-d9e7-4153-b40d-6459164cd9a9" />


**Question 6**
---
<img width="657" height="617" alt="Screenshot 2026-08-31 102431" src="https://github.com/user-attachments/assets/c1721814-8072-4593-9f9b-0e774459d56a" />


```sql
select InsuranceCompany,count(PatientId) as TotalPatients
from Insurance
group by InsuranceCompany;
```

**Output:**

<img width="772" height="777" alt="Screenshot 2026-08-31 102445" src="https://github.com/user-attachments/assets/a0068ac8-8bd0-46dc-9c9f-3ba1ba3469b4" />


**Question 7**
---
<img width="803" height="502" alt="Screenshot 2026-08-31 102538" src="https://github.com/user-attachments/assets/63a1a4c9-1f20-4ed8-aad4-c665719f505f" />


```sql
select PatientID,count(RecordID) as TotalRecords
from MedicalRecords
group by PatientID
having count(RecordID)>3;

```

**Output:**

<img width="757" height="430" alt="Screenshot 2026-08-31 102547" src="https://github.com/user-attachments/assets/d00cbcdd-f171-41cf-afcc-0809f534df68" />


**Question 8**
---
<img width="868" height="515" alt="Screenshot 2026-08-31 102652" src="https://github.com/user-attachments/assets/d9e5a64a-7c66-48d1-b8b5-26997a844faf" />


```sql
select category_id,count(*) as COUNT
from products
where category_id>2
group by category_id;
```

**Output:**

<img width="623" height="432" alt="Screenshot 2026-08-31 102700" src="https://github.com/user-attachments/assets/f3d056ad-9759-403e-a397-665123a7efb1" />


**Question 9**
---
<img width="842" height="527" alt="Screenshot 2026-08-31 102749" src="https://github.com/user-attachments/assets/88f33ed0-7810-4aad-9b18-84703e382e5a" />


```sql
select category_id,sum(price) as Total_Cost
from products
group by category_id
having sum(price)>50;
```

**Output:**

<img width="692" height="427" alt="Screenshot 2026-08-31 102757" src="https://github.com/user-attachments/assets/820878a1-b310-476e-b430-d4769e186fc6" />


**Question 10**
---
<img width="878" height="518" alt="Screenshot 2026-08-31 102902" src="https://github.com/user-attachments/assets/c12cf6a8-ec42-4762-a747-93bbe9a23572" />


```sql
select jdate,SUM(workhour)
from employee1
group by jdate
having sum(workhour)>40;
```

**Output:**


<img width="761" height="463" alt="Screenshot 2026-08-31 102910" src="https://github.com/user-attachments/assets/b302cb6b-e1dd-4a36-a7aa-c1f26c5fb847" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
