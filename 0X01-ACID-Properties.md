# Database Management System (DBMS) - ACID Properties

A transaction is a single logical unit of work that interacts with the database, performing a sequence of operations like reading, writing, updating, or deleting data.

Since databases are multi-user environments where multiple transactions can occur simultaneously, it is crucial to ensure data integrity, consistency, and reliability before, during, and after transactions.

To achieve this, ACID properties must be followed.

# ACID Properties in DBMS
ACID stands for:

A – Atomicity
C – Consistency
I – Isolation
D – Durability

These properties ensure that database transactions are executed properly and reliably, even in the case of errors, failures, or concurrent transactions.

## Atomicity (All or Nothing Rule)

Atomicity ensures that a transaction is executed completely or not at all. If any part of the transaction fails, the entire transaction is rolled back, and the database remains unchanged.

### Key Concepts

1. Commit: If a transaction successfully completes, all changes are permanently saved in the database.

2. Abort (Rollback): If a transaction fails, all changes are undone, leaving the database in its original state.

### Example:

Imagine you are transferring $100 from Account A to Account B in a banking system.

A transaction consists of two steps:

1. Debit $100 from Account A
2. Credit $100 to Account B

If the system crashes after the first step but before the second, money will be deducted from A but not added to B, leading to an inconsistent state.
With atomicity, the transaction is either fully completed or fully rolled back to ensure no partial updates occur.

## Consistency (Maintaining Data Integrity)

Consistency ensures that a database remains in a valid and stable state before and after a transaction. Any transaction must preserve the integrity constraints of the database.

### Key Concepts
1. A transaction must never leave the database in an inconsistent state.
2. Every transaction must transform the database from one valid state to another.

### Example:
Assume a database has a constraint that no account balance can be negative.
If a transaction attempts to withdraw $500 from an account with only $300, the transaction will be rejected to maintain consistency.

Consistency ensures that such invalid transactions are never committed.

## Isolation (Concurrency Control)

Isolation ensures that multiple transactions executing at the same time do not interfere with each other.

Without isolation, concurrent transactions could cause inconsistencies in the database.

### Key Concepts
1. Each transaction executes as if it is the only transaction running, even if multiple transactions are executing simultaneously.
2. Intermediate changes are not visible to other transactions until they are committed.
3. Isolation prevents issues such as dirty reads, non-repeatable reads, and phantom reads.

### Example:
Consider two users attempting to buy the last ticket for a concert at the same time:

User A starts a transaction and checks seat availability.

User B starts a transaction and also checks the same seat.

User A confirms and books the seat.

User B also tries to confirm the booking, but the seat is now unavailable.

With isolation, User B must wait for User A's transaction to complete before proceeding, preventing double booking.

## Isolation Levels
Databases allow different levels of isolation depending on how strict the system needs to be:

1. Read Uncommitted – Transactions can read uncommitted changes (not recommended).

2. Read Committed – Transactions can only read committed data.

3. Repeatable Read – Ensures the same data is read multiple times during a transaction.

4. Serializable – The strictest level, ensuring complete isolation between transactions.


## Durability (Permanent Storage of Changes)

Durability ensures that once a transaction is successfully completed (committed), its changes are permanently stored in the database, even in the event of a system crash or power failure.

### Key Concepts
 Data changes are written to disk and are not lost due to unexpected failures.

 The database ensures durability using techniques like write-ahead logging (WAL) and database backups.

### Example:
Imagine an online shopping website where a user purchases a laptop:

1. The user places an order.
2. The system confirms the order and saves the transaction.
3. A power failure occurs, shutting down the system.
4. When the system restarts, the order is still recorded in the database.

This is durability, ensuring that committed changes persist even after failures.

## Summary 

| **Property**  | **Ensures**  | **Example**  |
|--------------|------------|------------|
| **Atomicity**  | Transactions execute completely or not at all  | A failed money transfer reverts all changes |
| **Consistency**  | The database remains valid before and after transactions  | A negative account balance is prevented |
| **Isolation**  | Transactions do not interfere with each other  | Preventing double booking of a seat |
| **Durability**  | Committed transactions persist, even after failures  | An order remains saved after a crash |
