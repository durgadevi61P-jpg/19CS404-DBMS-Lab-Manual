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

<img width="782" height="541" alt="image" src="https://github.com/user-attachments/assets/7510964d-768f-4e82-932f-4446944dd5aa" />


### Entities and Attributes

<img width="717" height="388" alt="image" src="https://github.com/user-attachments/assets/65fadf1c-9335-4742-8311-d8eea8a3d6eb" />


### Relationships and Constraints

<img width="717" height="506" alt="image" src="https://github.com/user-attachments/assets/82f6474c-7c8c-4ae4-83c1-368f8e66ccd0" />


### Assumptions

Each member has a unique member_id. 
Programs are predefined (Yoga, Zumba, Weight Training).      
A member can join the same program only once at a time. 
Each personal training session is handled by only one trainer. 
Attendance is mandatory for every booked personal training session. 
Payments include both membership fees and personal training session fees.

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
<img width="636" height="778" alt="image" src="https://github.com/user-attachments/assets/c88a3110-d092-48fb-99b2-728367a5c4bc" />


### Entities and Attributes

<img width="612" height="547" alt="image" src="https://github.com/user-attachments/assets/9014baa3-df0f-4e69-92a9-d180355c5576" />


### Relationships and Constraints

<img width="461" height="655" alt="image" src="https://github.com/user-attachments/assets/9f50bc48-69d8-40e0-a7de-84b206c7871d" />


### Assumptions

Each member is uniquely registered. 
A member can borrow many books; each loan is for one book. 
A book can be loaned many times, but only once at a time. 
Loan stores start and return dates. 
Fine is generated only for late returns (one fine per loan). 
Events can have many speakers and many members. 
Each event is booked in one room; rooms can host many events. 
Members can attend multiple events. 

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

<img width="567" height="652" alt="image" src="https://github.com/user-attachments/assets/4943ed3a-fc10-4f56-8053-72545a607f36" />


### Entities and Attributes

<img width="566" height="522" alt="image" src="https://github.com/user-attachments/assets/5bebc029-7edd-4808-b63a-27f6db6b6e69" />

### Relationships and Constraints

<img width="570" height="172" alt="image" src="https://github.com/user-attachments/assets/daf24a15-64da-4fd4-a7c7-c29c139ea8ea" />
<img width="570" height="253" alt="image" src="https://github.com/user-attachments/assets/5fe5594d-ac32-429a-93b5-ee6f86912ffd" />


### Assumptions
Each Customer is uniquely identified by Customer_ID. 
A customer can place multiple orders, but each order belongs to one customer. 
A customer can make multiple reservations. 
Each Reservation is for one table at a specific date and time. 
A Table can be reserved many times, but only once at a given time. 
Each reservation is served by one waiter. 
A waiter can serve multiple reservations. 
Each reservation generates one bill. 
Each bill belongs to one reservation. 
## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
