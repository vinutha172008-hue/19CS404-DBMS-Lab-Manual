# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="738" height="221" alt="Screenshot 2026-08-21 121759" src="https://github.com/user-attachments/assets/38172e12-f71a-4bfe-bfc1-f1a75e5db8f9" />

```sql
CREATE TABLE Employees(
EmployeeID INTEGER PRIMARY KEY,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email TEXT UNIQUE,
Salary INTEGER CHECK(Salary>0),
DepartmentID INTEGER,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```
**Output:**

<img width="1260" height="519" alt="Screenshot 2026-08-21 121919" src="https://github.com/user-attachments/assets/444e59a5-3c26-475e-8da4-628d749ceaa8" />


**Question 2**
---
<img width="892" height="278" alt="Screenshot 2026-08-21 122430" src="https://github.com/user-attachments/assets/aa2217e4-ba85-44bd-9c69-aa3c95d96534" />


```sql
alter table Student_details
add column Mobilenumber number;
```

**Output:**

<img width="1265" height="435" alt="Screenshot 2026-08-21 122448" src="https://github.com/user-attachments/assets/d387c3a6-d549-4a18-a39e-9e59488676c1" />


**Question 3**
---
<img width="715" height="250" alt="Screenshot 2026-08-21 122740" src="https://github.com/user-attachments/assets/82b7ae66-0586-4089-86c6-65568f7c9136" />


```sql
INSERT INTO  student_details(RollNo,Name,Gender,Subject,MARKS)
SELECT RollNo,Name,Gender,Subject,MARKS
FROM Archived_students
```

**Output:**

<img width="1219" height="364" alt="Screenshot 2026-08-21 122753" src="https://github.com/user-attachments/assets/028da847-51fc-4412-9139-849a246ec920" />


**Question 4**
---
<img width="857" height="280" alt="Screenshot 2026-08-21 122913" src="https://github.com/user-attachments/assets/73d22ac8-7685-4d9b-867c-876b8d2b15ce" />


```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK (LENGTH(icom_id)=4),
FOREIGN KEY (icom_id) REFERENCES company(com_id)
ON UPDATE CASCADE
ON DELETE CASCADE
);
```

**Output:**

<img width="1197" height="458" alt="Screenshot 2026-08-21 122925" src="https://github.com/user-attachments/assets/1528e59a-af99-42c9-9bf5-52fcb4d2df9f" />


**Question 5**
---
<img width="1083" height="374" alt="Screenshot 2026-08-21 123030" src="https://github.com/user-attachments/assets/0bdcdf2b-d096-4c1a-97ef-60ccad7f5995" />


```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,YearPublished)
SELECT ISBN,Title,Author,Publisher,YearPublished
FROM Out_of_print_books;

```

**Output:**

<img width="1236" height="374" alt="Screenshot 2026-08-21 123043" src="https://github.com/user-attachments/assets/cee88c41-8cf1-47ce-8db5-ec6fa589aac4" />


**Question 6**
---
<img width="1077" height="420" alt="Screenshot 2026-08-21 123142" src="https://github.com/user-attachments/assets/2bd8036f-5b3f-4255-977c-e15904568200" />


```sql
CREATE TABLE Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);

```

**Output:**

<img width="1256" height="482" alt="Screenshot 2026-08-21 123153" src="https://github.com/user-attachments/assets/e0c5ace3-3994-4108-80da-73f29cd60c15" />


**Question 7**
---
<img width="1200" height="395" alt="Screenshot 2026-08-21 123334" src="https://github.com/user-attachments/assets/cc768e98-6b31-4da5-ae74-8af91ea23635" />


```sql
ALTER TABLE Employees 
ADD Date_of_joining Date;
ALTER TABLE Employees
RENAME COLUMN job_title TO Designation;

```

**Output:**

<img width="1255" height="426" alt="Screenshot 2026-08-21 123349" src="https://github.com/user-attachments/assets/2493919b-6bd4-4ad6-a4ee-175224bf3c93" />


**Question 8**
---
<img width="1210" height="307" alt="Screenshot 2026-08-21 123457" src="https://github.com/user-attachments/assets/caf17652-82f1-464b-bd53-b765a0df0371" />


```sql
INSERT INTO Products VALUES(104,'Tablet','Electronics',100,50);
```

**Output:**
<img width="1230" height="361" alt="Screenshot 2026-08-21 123510" src="https://github.com/user-attachments/assets/975caee9-91af-4c45-b48b-51efda5fec1d" />


**Question 9**
---
<img width="1066" height="471" alt="Screenshot 2026-08-21 123556" src="https://github.com/user-attachments/assets/ef79ec9d-c247-4f4c-ad97-33ef8e036224" />


```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK (LENGTH(icom_id)=4),
FOREIGN KEY (icom_id) 
REFERENCES company(com_id)
ON UPDATE SET NULL
ON DELETE SET NULL
);
```

**Output:**

<img width="1250" height="461" alt="Screenshot 2026-08-21 123609" src="https://github.com/user-attachments/assets/b5e9f79f-2bac-4047-82a6-a6bee04108d3" />


**Question 10**
---
<img width="1129" height="297" alt="Screenshot 2026-08-21 123702" src="https://github.com/user-attachments/assets/743bd313-b4cf-44b7-9282-fecfdf740c47" />


```sql
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES Orders(ORderID)
);
```

**Output:**

<img width="1304" height="282" alt="Screenshot 2026-08-21 123714" src="https://github.com/user-attachments/assets/68d1022f-b275-420e-a3a2-62d170619cd7" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
