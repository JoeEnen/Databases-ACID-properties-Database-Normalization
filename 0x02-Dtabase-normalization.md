# Database Management System (DBMS)

## ACID Properties

A transaction in a Database Management System (DBMS) is a logical unit of work that interacts with the database, performing read and write operations. For the database to maintain integrity and correctness, transactions must adhere to ACID properties:

### Atomicity (All or Nothing Rule)
Ensures that a transaction is either fully executed or not executed at all.

If any part of a transaction fails, the entire transaction is rolled back.

#### Key Operations:

Abort → If a transaction aborts, changes are not saved.

Commit → If a transaction commits, changes are permanently recorded.

Example: If a customer transfers money from one account to another, either both the debit and credit operations complete successfully, or neither takes effect.

### Consistency
Ensures that a database starts and ends in a valid state before and after a transaction.

Maintains database rules (constraints, relationships, etc.).

Prevents invalid transactions from corrupting the database.

### Isolation
Ensures that concurrent transactions do not interfere with each other.

Changes made in one transaction are not visible to another transaction until they are committed.

This prevents issues like dirty reads, non-repeatable reads, and phantom reads.

Example: In an airline reservation system, two users cannot book the same seat at the same time.

### Durability
Ensures that once a transaction is committed, its changes persist even in case of system failure.

Uses non-volatile storage (e.g., disks, logs, backups).

Example: If a user places an order in an e-commerce website, even if the system crashes, the order remains in the database.


## Database Normalization

Normalization is a systematic approach to organizing database tables to:
1. Reduce data redundancy
2. Improve efficiency and data integrity
3. Make data management simpler

Normalization splits a large table into smaller related tables while maintaining data relationships.

### Why Do We Need Normalization?

If a database is not normalized, it may suffer from the following anomalies:

| **Anomaly Type**      | **Issue**                                   | **Example**                                              |
|----------------------|------------------------------------------|------------------------------------------------------|
| **Insertion Anomaly** | Cannot insert new data due to missing values | A student cannot be added without assigning them a course |
| **Deletion Anomaly**  | Deleting a record removes useful data   | Deleting a student record also removes course details |
| **Update Anomaly**    | Inconsistent data updates               | Changing an instructor's name in one place but not in others |


Example of a Poorly Designed Table (Unnormalized Form - UNF):

| StudentID | Name    | Course  | Instructor  |
|-----------|--------|---------|-------------|
| 101       | Alice  | DBMS    | Prof. John  |
| 102       | Bob    | DBMS    | Prof. John  |
| 103       | Carol  | AI      | Prof. Smith |

If Prof. John changes his name, we must update multiple rows, increasing the risk of inconsistencies.


### Prerequisites for Normalization

1. Keys (Unique Identifiers)

A Primary Key (PK) uniquely identifies each record in a table.

A Foreign Key (FK) links tables together, ensuring relationships.

2. Functional Dependency

Helps define the relationship between data in a table.

If A → B, then B depends on A.

### Steps of Database Normalization

#### 1NF (First Normal Form)

a. Eliminate duplicate columns in a table.
b. Ensure atomicity (each field should contain indivisible values).
c. Identify a primary key.

#### NF (Second Normal Form)

Must be in 1NF.

Remove partial dependencies (all non-key attributes must depend on the entire primary key).

#### 3NF (Third Normal Form)

Must be in 2NF.

Remove transitive dependencies (attributes must depend only on the primary key).

## Additional Normalization Concepts

### Dependency-Preserving Decomposition

Ensures that functional dependencies remain enforceable without excessive joins.

### Lossless Decomposition

Ensures that when a table is split, joining them reconstructs the original data without losing information.

## Features of Database Normalization

| **Feature**                         | **Description**                                                   |
|--------------------------------------|-------------------------------------------------------------------|
| **Elimination of Data Redundancy**   | Reduces repetition of data in different parts of the database    |
| **Ensuring Data Consistency**        | Prevents inconsistent data from appearing in the database        |
| **Simplification of Data Management**| Makes data easier to update and retrieve                         |
| **Improved Database Design**         | Organizes data in a structured manner, making it flexible        |
| **Avoidance of Update Anomalies**    | Ensures updates are correctly propagated across records          |
| **Standardization**                  | Creates a uniform and consistent data model                      |


