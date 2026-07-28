# Chapter 14: JDBC Interview Questions

## 📖 Overview

This chapter contains the most frequently asked **JDBC interview questions**, covering beginner, intermediate, and advanced concepts. These questions will help you prepare for Java developer interviews.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Revise core JDBC concepts
- Answer interview questions confidently
- Understand practical JDBC scenarios
- Prepare for technical interviews

---

# Beginner Questions

### 1. What is JDBC?

**Answer:**

JDBC (Java Database Connectivity) is a Java API used to connect Java applications with relational databases and perform CRUD operations.

---

### 2. What are the main components of JDBC?

**Answer:**

- DriverManager
- Connection
- Statement
- PreparedStatement
- CallableStatement
- ResultSet

---

### 3. What is a JDBC Driver?

**Answer:**

A JDBC Driver is a software component that enables Java applications to communicate with a database.

---

### 4. What is the difference between executeQuery() and executeUpdate()?

| executeQuery() | executeUpdate() |
|---------------|-----------------|
| Used for SELECT | Used for INSERT, UPDATE, DELETE |
| Returns ResultSet | Returns affected row count |

---

### 5. What is ResultSet?

**Answer:**

A `ResultSet` stores the rows returned by a SQL query and allows the application to read them one by one.

---

### 6. What is PreparedStatement?

**Answer:**

`PreparedStatement` is a precompiled SQL statement that supports parameters, improves performance, and prevents SQL Injection.

---

### 7. Why is PreparedStatement preferred over Statement?

**Answer:**

- Prevents SQL Injection
- Faster for repeated execution
- Supports parameterized queries
- Easier to maintain

---

### 8. What is CallableStatement?

**Answer:**

`CallableStatement` is used to execute Stored Procedures from Java.

---

### 9. What is SQL Injection?

**Answer:**

SQL Injection is a security vulnerability where malicious user input changes the intended SQL query.

---

### 10. How can SQL Injection be prevented?

**Answer:**

By using `PreparedStatement` with parameterized queries.

---

# Intermediate Questions

### 11. What is Auto-Commit?

**Answer:**

Auto-Commit is the default JDBC mode where every SQL statement is committed automatically after execution.

---

### 12. What is a Transaction?

**Answer:**

A transaction is a group of SQL operations executed as a single unit of work.

---

### 13. Difference between commit() and rollback()?

| commit() | rollback() |
|-----------|------------|
| Saves changes | Undoes changes |
| Permanent | Restores previous state |

---

### 14. What are ACID properties?

**Answer:**

- **Atomicity**
- **Consistency**
- **Isolation**
- **Durability**

These ensure reliable and consistent database transactions.

---

### 15. What is Batch Processing?

**Answer:**

Batch Processing executes multiple SQL statements together to improve performance and reduce database communication.

---

### 16. What is Connection Pooling?

**Answer:**

Connection Pooling maintains reusable database connections, reducing the overhead of repeatedly creating new connections.

---

### 17. What is HikariCP?

**Answer:**

HikariCP is a fast, lightweight, and widely used JDBC connection pool implementation.

---

### 18. What is ResultSetMetaData?

**Answer:**

It provides metadata about the columns in a `ResultSet`, such as column names, types, and count.

---

### 19. What is try-with-resources?

**Answer:**

A Java feature that automatically closes resources such as `Connection`, `PreparedStatement`, and `ResultSet`.

---

### 20. Why should database credentials not be hardcoded?

**Answer:**

Because it creates security risks and makes applications difficult to maintain.

---

# Advanced Questions

### 21. Explain the JDBC architecture.

**Answer:**

Java Application → JDBC API → JDBC Driver → Database

---

### 22. How does Connection Pooling improve performance?

**Answer:**

Connections are created once and reused, reducing connection creation overhead and improving scalability.

---

### 23. What happens when close() is called on a pooled connection?

**Answer:**

The connection is returned to the connection pool instead of being physically closed.

---

### 24. What is the difference between Statement, PreparedStatement, and CallableStatement?

| Feature | Statement | PreparedStatement | CallableStatement |
|---------|-----------|-------------------|-------------------|
| Static SQL | ✅ | ❌ | ❌ |
| Parameters | ❌ | ✅ | ✅ |
| Stored Procedures | ❌ | ❌ | ✅ |
| SQL Injection Protection | ❌ | ✅ | ✅ |

---

### 25. What are the common causes of SQLException?

**Answer:**

- Invalid SQL syntax
- Connection failure
- Constraint violations
- Missing tables
- Network issues

---

### 26. How do you improve JDBC performance?

**Answer:**

- Use `PreparedStatement`
- Use Connection Pooling
- Execute batch operations
- Keep transactions short
- Retrieve only required columns
- Use indexes effectively

---

### 27. What are JDBC best practices?

**Answer:**

- Use `PreparedStatement`
- Use try-with-resources
- Configure Connection Pooling
- Handle exceptions properly
- Use transactions
- Validate user input
- Store credentials securely

---

### 28. Explain the DAO Pattern.

**Answer:**

The DAO (Data Access Object) pattern separates database logic from business logic, making applications easier to maintain and test.

---

### 29. Which Connection Pool is most commonly used today?

**Answer:**

HikariCP is the most popular choice because of its high performance and low memory usage.

---

### 30. What is the lifecycle of a JDBC application?

```text
Load Driver
      │
      ▼
Open Connection
      │
      ▼
Create Statement
      │
      ▼
Execute SQL
      │
      ▼
Process Result
      │
      ▼
Close Resources
```

---

# Quick Interview Tips

- Prefer `PreparedStatement` over `Statement`.
- Explain concepts with practical examples.
- Mention Connection Pooling in enterprise applications.
- Highlight transaction management for data consistency.
- Use try-with-resources for automatic resource management.
- Focus on security, performance, and maintainability.

---

# Summary

In this chapter, you learned:

- Core JDBC interview questions
- Transaction-related questions
- Connection Pooling concepts
- Performance optimisation
- Enterprise best practices

---

# Quick Revision

- JDBC connects Java applications to databases.
- `PreparedStatement` is preferred for security and performance.
- Transactions ensure data consistency.
- Connection Pooling improves scalability.
- Batch Processing improves bulk operation performance.
- HikariCP is the most commonly used connection pool.
- try-with-resources simplifies resource management.

---

# Practice Exercise

Prepare answers for the following:

1. Explain the JDBC architecture with a diagram.
2. Compare `Statement`, `PreparedStatement`, and `CallableStatement`.
3. Demonstrate transaction management with `commit()` and `rollback()`.
4. Explain how Connection Pooling works using HikariCP.
5. Build a small CRUD application using JDBC and explain its workflow in an interview.
