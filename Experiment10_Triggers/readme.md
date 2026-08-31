# Experiment 10: PL/SQL – Triggers

## AIM
To write and execute PL/SQL trigger programs for automating actions in response to specific table events like INSERT, UPDATE, or DELETE.

---

## THEORY

A **trigger** is a stored PL/SQL block that is automatically executed or fired when a specified event occurs on a table or view. Triggers can be used for enforcing business rules, auditing changes, or automatic updates.

### Types of Triggers:
- **Before Trigger**: Executes before the operation (INSERT, UPDATE, DELETE).
- **After Trigger**: Executes after the operation.
- **Row-level Trigger**: Executes for each affected row.
- **Statement-level Trigger**: Executes once for the triggering statement.

**Basic Syntax:**
```sql
CREATE OR REPLACE TRIGGER trigger_name
BEFORE|AFTER INSERT|UPDATE|DELETE ON table_name
[FOR EACH ROW]
BEGIN
   -- trigger logic
END;
```

## 1. Write a trigger to log every insertion into a table.
**Steps:**
- Create two tables: `employees` (for storing data) and `employee_log` (for logging the inserts).
- Write an **AFTER INSERT** trigger on the `employees` table to log the new data into the `employee_log` table.
## program
<img width="741" height="451" alt="Screenshot 2026-08-31 231530" src="https://github.com/user-attachments/assets/1a265031-e717-419c-85fb-08c67df3dde4" />


**Expected Output:**
- A new entry is added to the `employee_log` table each time a new record is inserted into the `employees` table.
## output
<img width="551" height="141" alt="Screenshot 2026-08-31 231602" src="https://github.com/user-attachments/assets/6cc5781d-5ca8-461d-a5ef-50d12d2d41ac" />


---

## 2. Write a trigger to prevent deletion of records from a sensitive table.
**Steps:**
- Write a **BEFORE DELETE** trigger on the `sensitive_data` table.
- Use `RAISE_APPLICATION_ERROR` to prevent deletion and issue a custom error message.
## program
<img width="807" height="331" alt="Screenshot 2026-08-31 232410" src="https://github.com/user-attachments/assets/41b67c25-320f-449c-9dd5-a169d216e4af" />


**Expected Output:**
- If an attempt is made to delete a record from `sensitive_data`, an error message is raised, e.g., `ERROR: Deletion not allowed on this table.`
## output
<img width="815" height="427" alt="Screenshot 2026-08-31 232353" src="https://github.com/user-attachments/assets/6f4c27f7-0d1a-4b8d-9452-f2399ae3e9b3" />


---

## 3. Write a trigger to automatically update a `last_modified` timestamp.
**Steps:**
- Add a `last_modified` column to the `products` table.
- Write a **BEFORE UPDATE** trigger on the `products` table to set the `last_modified` column to the current timestamp whenever an update occurs.
## program
<img width="582" height="437" alt="Screenshot 2026-08-31 232709" src="https://github.com/user-attachments/assets/e7263ce4-bcd8-4e94-8ecc-3f835f39cf08" />


**Expected Output:**
- The `last_modified` column in the `products` table is updated automatically to the current date and time when any record is updated.
## output
<img width="897" height="176" alt="Screenshot 2026-08-31 232723" src="https://github.com/user-attachments/assets/27bede98-9b63-4602-b8ca-d1e8f3439e47" />


---

## 4. Write a trigger to keep track of the number of updates made to a table.
**Steps:**
- Create an `audit_log` table with a counter column.
- Write an **AFTER UPDATE** trigger on the `customer_orders` table to increment the counter in the `audit_log` table every time a record is updated.
## program


**Expected Output:**
- The `audit_log` table will maintain a count of how many updates have been made to the `customer_orders` table.
## output


---

## 5. Write a trigger that checks a condition before allowing insertion into a table.
**Steps:**
- Write a **BEFORE INSERT** trigger on the `employees` table to check if the inserted salary meets a specific condition (e.g., salary must be greater than 3000).
- If the condition is not met, raise an error to prevent the insert.

**Expected Output:**
- If the inserted salary in the `employees` table is below the condition (e.g., salary < 3000), the insert operation is blocked, and an error message is raised, such as: `ERROR: Salary below minimum threshold.`

## RESULT
Thus, the PL/SQL trigger programs were written and executed successfully.
