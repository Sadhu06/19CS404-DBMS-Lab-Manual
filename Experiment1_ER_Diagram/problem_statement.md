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

<img width="1855" height="926" alt="image" src="https://github.com/user-attachments/assets/7c23faf4-5251-4cf7-8f04-17ded1d48bcb" />


### Entities and Attributes


| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| Member | Member ID (PK), Member Name, Membership Type, Start Date | Each member has a unique Member ID |
| Program | Program ID (PK), Program Name | Each fitness program has a unique Program ID |
| Trainer | Trainer ID (PK), Trainer Name, Trainer Duty Time | Each trainer has a unique Trainer ID |
| Training Session | Session ID (PK), Session Date, Session Time, Trainer ID (FK), Member ID (FK) | Links members and trainers for each session |
| Attendance | Attendance ID (PK), Member ID (FK), Status | Tracks attendance for members |
| Payment | Payment ID (PK), Member ID (FK), Amount | Tracks each payment transaction |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Attends | Member:N, Program:N | Total (Mandatory) | Members may attend multiple programs. |
| Teach Programs | Trainer:N, Program:N | Partial | Trainers may teach multiple programs. |
| Attend Sessions | Member:N, Training Session:N | Partial | Members may attend several sessions. |
| Allotted to (Trainer) | Member:1, Trainer:N | Partial | Trainers are allotted to several members. |
| Mark Attendance | Member:1, Attendance:N | Total | Attendance is tracked for each member. |
| Pay for Membership | Member:1, Payment:N | Partial | Members can have multiple payment records. |
| Training Session–Trainer | Trainer:1, Training Session:N | Total | Each training session is supervised by one trainer. |
| Training Session–Member | Member:1, Training Session:N | Total | Each training session is attended by one member. |


### Assumptions

Each entity’s primary key is unique and referenced by their respective foreign key.

A Training Session is assumed to involve one member and one trainer, but can be extended for group sessions.

Attendance marking is performed per session or per day for each member.

Payment details are linked directly to individual members.

Trainers may be allotted multiple members and can teach multiple programs.

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

<img width="1728" height="828" alt="image" src="https://github.com/user-attachments/assets/77d98a17-068a-4126-8e90-6fddac93d5ff" />



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| MEMBER | Member ID (PK), Name, Phone No., Membership Type | Each member has a unique ID. |
| BOOK | Book ID (PK), Book Title, Category, Availability | Each book has a unique ID. |
| BORROW | Borrow ID (PK), Member ID (FK), Book ID (FK), Loan Date, Return Date, Fine Amount | Links members and borrowed books. |
| EVENT | Event ID (PK), Event Name, Event Date, Event Type | Each event has a unique ID. |
| ROOM | Room ID (PK), Room Name, Location, Capacity | Each room has a unique ID. |
| SPEAKER | Speaker ID (PK), Name, Expertise, Contact Number | Each speaker has a unique ID. |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Members Have Borrow Records | MEMBER:1, BORROW:N | Total | Each member can have multiple borrow records. |
| Book Is Borrowed | BOOK:1, BORROW:N | Partial | A book can be borrowed multiple times. |
| Member Registers Event | MEMBER:N, EVENT:N | Optional | Members can register for multiple events. |
| Participate | EVENT:N, SPEAKER:N | Optional | Events may feature multiple speakers. |
| Event Held in Room | EVENT:1, ROOM:1 | Total | Each event is held in exactly one room; a room may host multiple events over time. |

### Assumptions

Each primary key is unique in its entity and properly referenced by foreign keys.

One borrow event links one member and one book; multiple borrow events per member or book are allowed.

Event registration by members can be many-to-many.

Multiple speakers can participate in a single event.

Each event is held in exactly one room, though rooms may host many events.

Book availability is managed by the system and updated upon each borrow/return.

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

<img width="1850" height="875" alt="image" src="https://github.com/user-attachments/assets/ad1ea1c8-7942-41f4-b9bb-8414ea2a5bc4" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| CUSTOMER | Customer ID (PK), Name, Email, Phone No. | Each customer has a unique ID. |
| RESERVATION | Reservation ID (PK), Customer ID (FK), Time, No. of Guests, Date | Each reservation links to a customer. |
| BILL | Bill ID (PK), Reservation ID (FK), Waiter ID (FK), Bill Amount, Bill Tax | Each bill refers to a reservation and is handled by a waiter. |
| WAITER | Waiter ID (PK), Name, Duty Time | Each waiter has a unique ID. |
| ORDER | Order ID (PK), Reservation ID (FK), Order Date, Order Amount | Each order is linked to a reservation. |
| DISH | Dish ID (PK), Name, Category, Price | Each dish has a unique ID. |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Makes Reservation | CUSTOMER:1, RESERVATION:N | Mandatory | Each customer can make multiple reservations. |
| Generates Bill | RESERVATION:1, BILL:1, WAITER:1 | Mandatory | Every reservation generates exactly one bill, handled by one waiter. |
| Served By | RESERVATION:1, WAITER:N | Mandatory | A waiter can handle multiple reservations. |
| Places Order | RESERVATION:1, ORDER:N | Optional | Each reservation can have multiple orders. |
| Includes | ORDER:N, DISH:N | Optional | An order can include multiple dishes, and a dish can appear in many orders. |


### Assumptions

Each primary key is unique and referenced as foreign keys where applicable.

A reservation is associated with exactly one customer, and may be handled by one or more waiters.

Orders are associated with reservations; each order can include multiple dishes.

A bill is generated per reservation, and handled by a specific waiter.

Cardinality is mostly one-to-many from customer to reservation/orders, and many-to-many from orders to dishes.

All data entities and relationships reflect the diagram structure and relational schema.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
