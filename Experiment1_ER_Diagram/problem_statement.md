# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1392" height="787" alt="WhatsApp Image 2026-07-26 at 11 41 00 PM" src="https://github.com/user-attachments/assets/9209a1be-d185-46b6-8df2-13491e6eb643" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Trainer|trainer_id (PK), name, specialization, phone_no                    |    Represents trainers who conduct fitness programs.   |
| Program       | program_id (PK), name, category                 |Defines the fitness programs offered.       |
| Member       |  member_id (PK), name, email, member_type                  |Represents registered gym members.       |
| Session       | session_id (PK), session_time, session_type                 | Represents personal training sessions.      |
|Attendance        |  attendance_id (PK), date, status                 | Stores attendance details for each session.      |
|Payment |  payment_id (PK), member_id (FK), payment_type  |  Stores payment details of members. |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Trainer – Program             | M:N           |  Mandatory             |A trainer teaches multiple programs, and a program may be taught by multiple trainers.       |
| Member – Program             | M:N           |  Optional             | A member may join multiple programs.      |
| Trainer – Session             |  1:M          |  Mandatory             |  One trainer handles many sessions.     |
|Member – Session            |     1:M       |   Optional            | A member can book multiple sessions.      |
| Session – Attendance           |  1:M          |     Mandatory          |  Every session has attendance records.     |
|  Member – Payment          |   1:M         |   Mandatory            |  A member can make multiple payments.     |

### Assumptions
- Every trainer can teach one or more programs.
- Members may join multiple fitness programs.
- Attendance is recorded for every session
- Payments are made only by registered members.
---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="1422" height="772" alt="WhatsApp Image 2026-07-27 at 7 25 08 AM" src="https://github.com/user-attachments/assets/d4c8121f-d970-4747-a2af-9392301e381f" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Speaker        | speaker_id (PK), name, specialization                   |Represents speakers for library events.       |
| Member       | member_id (PK), name, email                   | Represents registered library members.      |
| Event       |  event_id (PK), name, date                  | Represents library events.      |
| Book       |  book_id (PK), title, author, category                  | Represents books available in the library.      |
| Loan       |   loan_id (PK), loan_date, return_date                 | Stores borrowing details of books.      |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|  Speaker – Event            | 1:M           | Mandatory              | One speaker can conduct multiple events.      |
|Member – Event              | M:N           |  Optional             | A member may register for multiple events.      |
| Member – Loan             | 1:M           | Mandatory              |  A member can borrow multiple books through loans.     |
| Book – Loan             |   1:M         |   Mandatory            | A book can be associated with multiple loans over time      |

### Assumptions
- Only registered members can borrow books.
- Members may register for multiple events.
- Every event has at least one speaker.
- A book can be borrowed many times at different periods.
---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1342" height="692" alt="WhatsApp Image 2026-07-27 at 7 59 20 AM" src="https://github.com/user-attachments/assets/528f1390-1013-4f9b-ab8a-facc3573f7a5" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Customer       |   customer_id (PK), name, email, phone_no                 | Represents restaurant customers.      |
| Reservation       |   reservation_id (PK), date_and_time, type, no_of_guests                 |  Stores reservation details.     |
|  Waiter      |    waiter_id (PK), name, phone                | Represents restaurant waiters.      |
| Order       |   order_id (PK), date, total_amount                 |  Stores order details.     |
|  Dish    |    dish_id (PK), dish_name, category, price                |  Represents dishes available in the restaurant.     |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Customer – Reservation              | 1:M           | Mandatory              | A customer can make multiple reservations.      |
| Waiter – Reservation             | 1:M           |    Mandatory           |   One waiter serves multiple reservations.    |
| Reservation – Order             |   1:M         |     Mandatory          |   A reservation can have multiple orders.    |
|Order – Dish              |     M:N       |        Mandatory       |    An order contains multiple dishes, and a dish can be part of multiple orders.   |
### Assumptions
- Only customers can make reservations.
- Every reservation is served by one waiter
- Multiple dishes can be included in a single order.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
