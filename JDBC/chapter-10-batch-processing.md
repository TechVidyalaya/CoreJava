# Chapter 10: Batch Processing

## 📖 Overview

**Batch Processing** allows multiple SQL statements to be grouped together and executed as a single batch. Instead of sending one SQL statement at a time, JDBC sends all statements together, improving performance and reducing database communication.

Batch processing is commonly used when inserting or updating thousands of records.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Batch Processing
- Add SQL statements to a batch
- Execute batches efficiently
- Improve database performance
- Handle batch exceptions
- Follow best practices

---

# What is Batch Processing?

Batch Processing is the execution of multiple SQL statements together in one database call.

Instead of:

```text
Insert Record 1
Insert Record 2
Insert Record 3
Insert Record 4
```

We send all records together as a single batch.

---

# Why Use Batch Processing?

Benefits:

- Faster execution
- Fewer database calls
- Better network utilisation
- Reduced execution time
- Improved performance for large datasets

---

# Batch Processing Workflow

```text
Java Application
        │
        ▼
Add Statements
        │
        ▼
Create Batch
        │
        ▼
Execute Batch
        │
        ▼
Database
```

---

# Adding Statements to a Batch

```java
Statement statement =
    connection.createStatement();

statement.addBatch(
    "INSERT INTO students VALUES (101,'Rahul','Java',90)"
);

statement.addBatch(
    "INSERT INTO students VALUES (102,'Amit','Python',88)"
);

statement.addBatch(
    "INSERT INTO students VALUES (103,'Priya','SQL',91)"
);
```

---

# Executing the Batch

```java
int[] result =
    statement.executeBatch();
```

Output:

```text
[1, 1, 1]
```

Each value represents the number of affected rows.

---

# Clearing the Batch

```java
statement.clearBatch();
```

This removes all SQL statements from the batch.

---

# Batch Processing with PreparedStatement

```java
String sql =
    "INSERT INTO students VALUES (?, ?, ?, ?)";

PreparedStatement ps =
    connection.prepareStatement(sql);
```

---

# Adding Records

```java
ps.setInt(1, 101);
ps.setString(2, "Rahul");
ps.setString(3, "Java");
ps.setInt(4, 90);

ps.addBatch();

ps.setInt(1, 102);
ps.setString(2, "Amit");
ps.setString(3, "Python");
ps.setInt(4, 88);

ps.addBatch();
```

---

# Execute PreparedStatement Batch

```java
int[] result =
    ps.executeBatch();
```

---

# Batch with Transaction

```java
connection.setAutoCommit(false);

ps.executeBatch();

connection.commit();
```

If an error occurs:

```java
connection.rollback();
```

---

# Batch Processing Lifecycle

```text
Create Statement
        │
        ▼
Add SQL Statements
        │
        ▼
Execute Batch
        │
        ▼
Commit Transaction
        │
        ▼
Close Resources
```

---

# BatchUpdateException

If one of the batch statements fails, JDBC throws a `BatchUpdateException`.

Example:

```java
try {

    ps.executeBatch();

}
catch (BatchUpdateException e) {

    System.out.println(

        e.getMessage()

    );
}
```

---

# Statement vs Batch Processing

| Feature | Normal Execution | Batch Processing |
|---------|------------------|------------------|
| Database Calls | Multiple | Single |
| Performance | Lower | Higher |
| Network Usage | High | Low |
| Best For | Few records | Large datasets |

---

# Real-World Applications

Batch Processing is used in:

- Payroll systems
- Student result uploads
- Employee data imports
- Banking transactions
- Inventory updates
- Data migration

---

# Common Mistakes

### Forgetting addBatch()

Incorrect:

```java
ps.executeBatch();
```

Always add statements before executing.

---

### Forgetting executeBatch()

Adding records alone does not execute them.

```java
ps.addBatch();
```

Always call:

```java
ps.executeBatch();
```

---

### Ignoring Transactions

For critical operations, combine batch processing with transactions.

---

# Best Practices

- Prefer `PreparedStatement` for batch operations.
- Commit batches using transactions.
- Execute batches in manageable sizes for very large datasets.
- Handle `BatchUpdateException`.
- Clear the batch after execution.
- Close all JDBC resources.

---

# Summary

In this chapter, you learned:

- Batch Processing
- addBatch()
- executeBatch()
- clearBatch()
- BatchUpdateException
- Transactions with batches
- Best practices

---

# Quick Revision

- Batch Processing executes multiple SQL statements together.
- `addBatch()` adds SQL statements.
- `executeBatch()` executes all statements.
- `clearBatch()` removes queued statements.
- `PreparedStatement` is preferred for batch operations.
- Use transactions for reliability.
- Batch Processing improves performance significantly.

---

# Practice Questions

### Basic

1. What is Batch Processing?
2. Why is Batch Processing faster?
3. Which method adds SQL statements to a batch?
4. Which method executes the batch?
5. What does `clearBatch()` do?

### Intermediate

6. Explain Batch Processing using `PreparedStatement`.
7. Why should transactions be used with batch processing?
8. What is `BatchUpdateException`?

### Interview Questions

1. Explain Batch Processing in JDBC.
2. What is the difference between normal execution and batch execution?
3. Why is `PreparedStatement` preferred for batch processing?
4. How do you handle failures during batch execution?
5. What are the advantages and limitations of Batch Processing?

---

# Hands-on Exercise

Create a **Bulk Student Import** application that:

1. Create a `students` table.
2. Insert 20 student records using `PreparedStatement`.
3. Add each record using `addBatch()`.
4. Execute all inserts using `executeBatch()`.
5. Disable auto-commit and commit the transaction after successful execution.
6. Roll back the transaction if any insert fails.
7. Display the number of affected rows.
8. Compare the execution time of individual inserts versus batch inserts.
