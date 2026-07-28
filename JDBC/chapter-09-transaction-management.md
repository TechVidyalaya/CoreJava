# Chapter 09: Transaction Management

## 📖 Overview

A **transaction** is a group of one or more SQL operations executed as a single unit of work. If all operations succeed, the transaction is **committed**. If any operation fails, the transaction is **rolled back**, ensuring data consistency.

Transaction Management is essential for applications like banking, e-commerce, and inventory systems.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand transactions
- Learn ACID properties
- Use commit and rollback
- Manage auto-commit mode
- Handle transaction failures
- Follow transaction best practices

---

# What is a Transaction?

A transaction is a sequence of SQL operations treated as one logical unit.

Example:

- Withdraw money from Account A
- Deposit money into Account B

Both operations must succeed together.

---

# Transaction Workflow

```text
Start Transaction
        │
        ▼
Execute SQL Statements
        │
        ▼
All Successful?
   ┌──────────────┐
   │              │
 Yes             No
   │              │
   ▼              ▼
Commit         Rollback
```

---

# Auto-Commit Mode

By default, JDBC enables **Auto-Commit**.

```java
Connection connection =
    DriverManager.getConnection(
        url,
        user,
        password
    );

System.out.println(
    connection.getAutoCommit()
);
```

Output:

```text
true
```

Each SQL statement is committed automatically.

---

# Disabling Auto-Commit

To manage transactions manually:

```java
connection.setAutoCommit(false);
```

Now changes will not be saved until `commit()` is called.

---

# Commit Transaction

```java
connection.commit();
```

A commit permanently saves all changes made during the transaction.

---

# Rollback Transaction

```java
connection.rollback();
```

Rollback undoes all changes made since the last commit.

---

# Transaction Example

```java
try {

    connection.setAutoCommit(false);

    PreparedStatement withdraw =
        connection.prepareStatement(
            "UPDATE accounts SET balance = balance - ? WHERE id=?"
        );

    PreparedStatement deposit =
        connection.prepareStatement(
            "UPDATE accounts SET balance = balance + ? WHERE id=?"
        );

    // Execute statements

    connection.commit();

}
catch (SQLException e) {

    connection.rollback();
}
```

---

# Savepoints

A **Savepoint** allows partial rollback within a transaction.

```java
Savepoint sp =
    connection.setSavepoint();
```

Rollback to savepoint:

```java
connection.rollback(sp);
```

---

# ACID Properties

| Property | Description |
|----------|-------------|
| **Atomicity** | All operations succeed or none |
| **Consistency** | Database remains valid |
| **Isolation** | Transactions do not interfere |
| **Durability** | Committed data is permanent |

---

# Transaction Lifecycle

```text
Open Connection
       │
       ▼
Disable Auto-Commit
       │
       ▼
Execute SQL
       │
       ▼
Commit / Rollback
       │
       ▼
Close Connection
```

---

# Real-World Example

### Bank Transfer

Without a transaction:

- ₹5,000 deducted
- Deposit fails

Result:

- Money is lost.

With a transaction:

- Deduction fails → Rollback
- Both accounts remain consistent.

---

# Isolation Levels

JDBC supports different transaction isolation levels.

| Level | Description |
|--------|-------------|
| `READ_UNCOMMITTED` | Lowest isolation |
| `READ_COMMITTED` | Reads committed data only |
| `REPEATABLE_READ` | Prevents non-repeatable reads |
| `SERIALIZABLE` | Highest isolation |

Example:

```java
connection.setTransactionIsolation(

    Connection.TRANSACTION_READ_COMMITTED
);
```

---

# Common Mistakes

### Forgetting to Commit

```java
connection.setAutoCommit(false);
```

If `commit()` is not called, changes are not saved.

---

### Ignoring Rollback

If an exception occurs, always call:

```java
connection.rollback();
```

---

### Leaving Auto-Commit Disabled

Always restore auto-commit if the connection will be reused.

```java
connection.setAutoCommit(true);
```

---

# Best Practices

- Disable auto-commit for multi-step operations.
- Commit only after all operations succeed.
- Roll back immediately on failure.
- Keep transactions short.
- Use savepoints for complex transactions.
- Handle SQL exceptions properly.

---

# Summary

In this chapter, you learned:

- Transactions
- Auto-commit
- Commit
- Rollback
- Savepoints
- ACID properties
- Isolation levels
- Best practices

---

# Quick Revision

- A transaction is a group of SQL operations.
- Auto-commit is enabled by default.
- Use `setAutoCommit(false)` for manual transactions.
- `commit()` saves changes permanently.
- `rollback()` undoes changes.
- ACID ensures reliable transactions.
- Keep transactions short for better performance.

---

# Practice Questions

### Basic

1. What is a transaction?
2. What is auto-commit?
3. What does `commit()` do?
4. What does `rollback()` do?
5. What is a savepoint?

### Intermediate

6. Explain the ACID properties.
7. Why should auto-commit be disabled for banking transactions?
8. What is the purpose of transaction isolation levels?

### Interview Questions

1. Explain transaction management in JDBC.
2. What is the difference between auto-commit and manual commit?
3. Explain the ACID properties with examples.
4. When should savepoints be used?
5. How do transaction isolation levels affect concurrency?

---

# Hands-on Exercise

Create a **Bank Transfer System** that:

1. Create an `accounts` table with account ID and balance.
2. Insert sample account records.
3. Disable auto-commit.
4. Deduct an amount from one account.
5. Add the same amount to another account.
6. Commit the transaction if both operations succeed.
7. Roll back the transaction if any operation fails.
8. Experiment with savepoints and different transaction isolation levels.
