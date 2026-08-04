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
*Paste or attach your diagram here*  
<img width="1332" height="817" alt="seniero_1 drawio" src="https://github.com/user-attachments/assets/42bc280f-acb4-4a10-8c9f-05017570cecd" />

### Entities and Attributes

| Entity                        | Attributes (PK, FK)                                                            | Notes                                                |
| ----------------------------- | ------------------------------------------------------------------------------ | ---------------------------------------------------- |
| **Member**                    | **member_id (PK)**, name, membership_type, start_date                          | Stores gym member details                            |
| **Program**                   | **program_id (PK)**, program_name, duration                                    | Stores fitness program details                       |
| **Trainer**                   | **trainer_id (PK)**, trainer_name, specialization                              | Stores trainer information                           |
| **Personal_Training_Session** | **session_id (PK)**, member_id (FK), trainer_id (FK), session_date, attendance | Records personal training sessions booked by members |
| **Membership_Payment**        | **payment_id (PK)**, member_id (FK), amount, payment_date, payment_type        | Stores membership and session payment details        |



### Relationships and Constraints

| Relationship                                   | Cardinality | Participation | Notes                                                                                     |
| ---------------------------------------------- | ----------- | ------------- | ----------------------------------------------------------------------------------------- |
| Member **JOINS** Program                       | M : N       | Partial       | A member can join multiple programs, and a program can have multiple members.             |
| Trainer **ASSIGNED TO** Program                | M : N       | Partial       | A trainer may be assigned to multiple programs, and a program may have multiple trainers. |
| Member **BOOKS** Personal Training Session     | 1 : M       | Partial       | A member can book many sessions, but each session belongs to one member.                  |
| Trainer **CONDUCTS** Personal Training Session | 1 : M       | Partial       | A trainer can conduct many sessions, but each session is conducted by one trainer.        |
| Member **MAKES** Membership Payment            | 1 : M       | Total         | A member can make multiple payments, and every payment belongs to one member.             |


### Assumptions
- Each personal training session is conducted by exactly one trainer and booked by exactly one member.
- Attendance is recorded only for personal training sessions.
- Payments are linked to a single member and may include membership fees or personal training session charges.

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
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

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
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
