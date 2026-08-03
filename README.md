# ⚽ Football Ticket Booking System Database

A relational database project built with PostgreSQL that simulates a football ticket booking platform. The system manages users, football matches, and ticket bookings while enforcing data integrity through primary keys, foreign keys, unique constraints, and business-rule validations.

---

## 📌 Project Overview

This project was developed as part of a Database Management Systems assignment to demonstrate practical understanding of:

* Relational Database Design
* Entity Relationship Diagram (ERD)
* Primary & Foreign Keys
* Data Integrity Constraints
* SQL Querying
* Joins & Subqueries
* Aggregate Functions
* NULL Handling
* Pagination Techniques

The system allows football fans to purchase tickets for matches while maintaining a structured and normalized database architecture.

---

## 🏗️ Database Architecture

The database consists of three core entities:

### 👤 Users

Stores information about football fans and ticket managers.

| Column       | Constraint       |
| ------------ | ---------------- |
| user_id      | PRIMARY KEY      |
| full_name    | NOT NULL         |
| email        | UNIQUE, NOT NULL |
| role         | CHECK Constraint |
| phone_number | Optional         |

---

### ⚽ Matches

Stores football match information and ticket availability.

| Column              | Constraint       |
| ------------------- | ---------------- |
| match_id            | PRIMARY KEY      |
| fixture             | NOT NULL         |
| tournament_category | NOT NULL         |
| base_ticket_price   | CHECK (>= 0)     |
| match_status        | CHECK Constraint |

---

### 🎟️ Bookings

Stores ticket purchase transactions.

| Column         | Constraint       |
| -------------- | ---------------- |
| booking_id     | PRIMARY KEY      |
| user_id        | FOREIGN KEY      |
| match_id       | FOREIGN KEY      |
| seat_number    | Optional         |
| payment_status | CHECK Constraint |
| total_cost     | CHECK (>= 0)     |

---

## 🔗 Entity Relationships

### One-to-Many

A single user can make multiple bookings.

```text
User (1) -------- (M) Bookings
```

### Many-to-One

Multiple bookings can belong to a single football match.

```text
Bookings (M) -------- (1) Match
```

### Logical Relationship

Each booking record represents a specific user booking a specific match ticket.

---

## 📊 ERD Diagram

### Public ERD Link

https://drive.google.com/file/d/1OOsK1ZqLVqwLTXSbVhZIk7YWiTyfW2BM/view?usp=sharing

The ERD contains:

* Primary Keys
* Foreign Keys
* Relationship Cardinality
* Business Rule Constraints

---

## 🛡️ Data Integrity Rules

### Users

```sql
PRIMARY KEY (user_id)
UNIQUE (email)
CHECK (role IN ('Ticket Manager', 'Football Fan'))
```

### Matches

```sql
PRIMARY KEY (match_id)

CHECK (
  base_ticket_price >= 0
)

CHECK (
  match_status IN (
    'Available',
    'Selling Fast',
    'Sold Out',
    'Postponed'
  )
)
```

### Bookings

```sql
PRIMARY KEY (booking_id)

FOREIGN KEY (user_id)
REFERENCES Users(user_id)
ON DELETE CASCADE

FOREIGN KEY (match_id)
REFERENCES Matches(match_id)
ON DELETE CASCADE

CHECK (total_cost >= 0)

CHECK (
  payment_status IN (
    'Pending',
    'Confirmed',
    'Cancelled',
    'Refunded'
  )
)
```

---

## 🚀 Features Implemented

### Database Features

* Primary Key Constraints
* Foreign Key Constraints
* Unique Constraints
* CHECK Constraints
* Referential Integrity
* Cascading Delete Rules
* NULL Handling

### SQL Features

* Filtering with WHERE
* Pattern Matching using ILIKE
* INNER JOIN
* LEFT JOIN
* Aggregate Functions
* Subqueries
* COALESCE
* ORDER BY
* LIMIT
* OFFSET

---

## 📝 Implemented Queries

### Query 1

Retrieve all available Champions League matches.

**Concepts Used**

* WHERE
* AND Filtering

---

### Query 2

Search users by name pattern.

**Concepts Used**

* ILIKE
* Pattern Matching

---

### Query 3

Handle NULL payment status values.

**Concepts Used**

* COALESCE
* IS NULL

---

### Query 4

Retrieve booking details with user and match information.

**Concepts Used**

* INNER JOIN

---

### Query 5

Display all users including those without bookings.

**Concepts Used**

* LEFT JOIN

---

### Query 6

Find bookings above average booking cost.

**Concepts Used**

* Aggregate Function
* Subquery

---

### Query 7

Retrieve the most expensive matches while skipping the highest-priced match.

**Concepts Used**

* ORDER BY
* LIMIT
* OFFSET

---

## 📂 Project Structure

```text
football-ticket-booking-system/
│
├── README.md
├── schema.sql
├── queries.sql
└── ERD.png
```

---

## 💻 How to Run

### Clone Repository

```bash
git clone <repository-url>
```

### Create Database

```sql
CREATE DATABASE football_ticket_db;
```

### Connect Database

```sql
\c football_ticket_db
```

### Execute Schema & Queries

```sql
\i schema.sql
\i queries.sql
```

---

## 🎯 Key Learning Outcomes

Through this project I gained hands-on experience with:

* Database Normalization
* ERD Design
* Relational Data Modeling
* Referential Integrity
* SQL Query Optimization
* Join Operations
* Subqueries
* Aggregate Functions
* Constraint Management

---

## 👨‍💻 Author

**Md. Shoriful Islam**

Frontend Developer | Aspiring Full Stack Developer

### Technical Skills

* JavaScript
* TypeScript
* React.js
* Next.js
* Node.js
* Express.js
* PostgreSQL
* MongoDB
* Git & GitHub

---

## 📜 Academic Note

This project was developed as part of a Database Management Systems assignment and is intended for educational purposes. The implementation focuses on demonstrating database design principles, relational modeling, and SQL problem-solving techniques using PostgreSQL.
