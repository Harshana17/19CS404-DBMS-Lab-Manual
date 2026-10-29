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

<img width="1355" height="603" alt="image" src="https://github.com/user-attachments/assets/50ecf5ae-6052-4898-afce-f9df53bfe134" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| Member | Member_ID (PK), Name, Membership_Type, Start_Date | Stores details of gym members. |
| Program | Program_ID (PK), Program_Name, Category, Duration | Stores information about fitness programs such as Yoga, Zumba, and Weight Training. |
| Trainer | Trainer_ID (PK), Name, Qualification, Phone | Stores trainer information and specialization. |
| Personal_Session | Session_ID (PK), Session_Date, Session_Time, Member_ID (FK), Trainer_ID (FK) | Records personal training sessions booked by members. |
| Attendance | Attendance_ID (PK), Session_ID (FK), Member_ID (FK), Status | Records attendance for each personal training session. |
| Payment | Payment_ID (PK), Payment_Date, Amount, Payment_Method, Member_ID (FK) | Stores membership and personal session payment details. |
### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|----------------|-------|
| Member JOINS Program | M:N | Total – Partial | A member can join multiple programs, and a program can have many members. |
| Trainer ASSIGNED TO Program | M:N | Total – Total | A trainer can teach multiple programs, and a program can have multiple trainers. |
| Member BOOKS Personal Session | 1:N | Partial – Total | One member can book many personal training sessions; every session belongs to one member. |
| Trainer CONDUCTS Personal Session | 1:N | Partial – Total | One trainer can conduct many sessions; each session is conducted by one trainer. |
| Personal Session HAS Attendance | 1:N | Total – Total | Attendance is recorded for each session. |
| Member MAKES Payment | 1:N | Partial – Total | A member can make multiple payments; every payment belongs to one member. |

### Assumptions
1.	Every Member has a unique Member_ID. 
2.	Every Trainer has a unique Trainer_ID. 
3.	Every Program has a unique Program_ID. 
4.	A member may enroll in multiple programs. 
5.	A trainer may be assigned to multiple programs. 
6.	Each personal training session is conducted by one trainer for one member. 
7.	Attendance is recorded for each personal session. 
8.	Payments may be for either membership fees or personal training sessions.

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

<img width="1352" height="893" alt="image" src="https://github.com/user-attachments/assets/fc0c46ff-2335-48d5-b662-801ae247200f" />


### Entities and Attributes

| Entity            | Attributes (PK, FK)                                                                    | Notes                                                       |
| ----------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| **Member**        | **Member_ID (PK)**, Name, Email, Phone_No, Membership_Status                           | Stores information about library members.                   |
| **Book**          | **Book_ID (PK)**, Title, Author, Publisher, Edition, Language                          | Stores details of all books available in the library.       |
| **Borrow_Record** | **Borrow_ID (PK)**, Member_ID (FK), Book_ID (FK), Due_Date, Return_Date, Borrow_Status | Records every book borrowing transaction.                   |
| **Event**         | **Event_ID (PK)**, Event_Name, Event_Date, Start_Time, End_Time                        | Stores information about library events.                    |
| **Speaker**       | **Speaker_ID (PK)**, Speaker_Name, Qualification, Phone_No                             | Stores details of speakers/authors participating in events. |
| **Fine**          | **Payment_ID (PK)**, Borrow_ID (FK), Amount, Fine_Date, Payment_Date, Payment_Status   | Stores overdue fine details for late book returns.          |

### Relationships and Constraints


| Relationship                         | Cardinality | Participation                           | Notes                                                                                      |
| ------------------------------------ | ----------- | --------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Member — Borrows — Borrow_Record** | 1 : N       | Partial (Member), Total (Borrow_Record) | One member can have many borrow records; each borrow record belongs to one member.         |
| **Borrow_Record — For — Book**       | N : 1       | Total                                   | Each borrow record refers to one book; a book can appear in many borrow records over time. |
| **Borrow_Record — Generates — Fine** | 1 : 0..1    | Partial                                 | A borrow record generates a fine only if the book is returned late.                        |
| **Member — Registers — Event**       | M : N       | Partial                                 | Members may register for multiple events, and an event may have many registered members.   |
| **Event — Has — Speaker**            | M : N       | Total (Event), Partial (Speaker)        | Every event has one or more speakers, while a speaker may participate in multiple events.  |

### Assumptions
1.	Every member has a unique Member_ID. 
2.	Every book has a unique Book_ID. 
3.	A member can borrow multiple books, but each borrow record refers to only one book. 
4.	Borrow details such as loan date, due date, and return date are stored in Borrow_Record. 
5.	A fine is generated only if a book is returned after the due date. 
6.	Members can register for multiple events. 
7.	Each event may have multiple speakers. 
8.	A speaker may participate in multiple library events. 
9.	All primary keys are unique and cannot be NULL. 
10.	One borrow record can generate at most one fine.
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

<img width="3570" height="2328" alt="erdplus (2)" src="https://github.com/user-attachments/assets/36173127-2406-4a5b-9dca-7b0edb3e08b3" />


### Entities and Attributes


## Entities and Attributes

| Entity | Attributes |
|---|---|
| MEMBER | Member_ID (PK), Name, Phone, Email |
| MEMBERSHIP | Membership_ID (PK), Membership_Type, Start_Date, End_Date, Fee |
| PROGRAM | Program_ID (PK), Program_Name, Description |
| TRAINER | Trainer_ID (PK), Trainer_Name, Phone, Specialization |
| PERSONAL_SESSION | Session_ID (PK), Session_Date, Start_Time, Duration |
| ATTENDANCE | Attendance_ID (PK), Attendance_Status, Recorded_Date |
| PAYMENT | Payment_ID (PK), Amount, Payment_Date, Payment_Method |


### Relationships and Constraints

| Relationship | Cardinality | Constraints |
|---|---|---|
| MEMBER - MEMBERSHIP | 1:M | A member can have multiple membership records, and each membership belongs to one member. |
| MEMBER - PROGRAM | M:N | A member can join multiple programs, and a program can have multiple members. |
| TRAINER - PROGRAM | M:N | A trainer can handle multiple programs, and a program can have multiple trainers. |
| MEMBER - PERSONAL_SESSION | 1:M | A member can book multiple personal training sessions, and each session belongs to one member. |
| TRAINER - PERSONAL_SESSION | 1:M | A trainer can conduct multiple sessions, and each session is assigned to one trainer. |
| PERSONAL_SESSION - ATTENDANCE | 1:0..1 | A session may have zero or one attendance record, and each attendance record belongs to one session. |
| MEMBER - PAYMENT | 1:M | A member can make multiple payments, and each payment belongs to one member. |
| MEMBERSHIP - PAYMENT | 1:M | A membership can have multiple payment records, and each membership payment references one membership. |
| PERSONAL_SESSION - PAYMENT | 1:M | A session can have multiple payment records, and each session payment references one session. |


### Assumptions

1.Each member is identified by a unique Member_ID.

2.A member can have multiple membership records over time.

3.The gym offers multiple fitness programs, such as Yoga, Zumba, and Weight Training.

4.Members can enroll in multiple programs, and each program can have multiple members.

5.Trainers can be assigned to multiple programs, and each program can have multiple trainers.

6.Each personal training session is booked by one member and conducted by one trainer.

7.Attendance is recorded separately for each personal training session.

8.A session may not yet have an attendance record if it has not taken place.

9.Payments are recorded separately for membership fees and personal training sessions.

10.Each payment belongs to one member and is linked to either a membership or a personal training session, but not both.

11.A member can make multiple payments for a membership or a personal training session.


## Result:

The ER diagrams for the City Fitness Club Management System, City Library Event & Book Lending System, and Restaurant Table Reservation & Ordering System were successfully designed based on the given business requirements.

