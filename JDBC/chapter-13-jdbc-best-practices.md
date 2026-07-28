# Chapter 13: JDBC Best Practices

## 📖 Overview

Writing JDBC code is not just about connecting to a database. Good coding practices improve **performance, security, readability, maintainability, and reliability**.

This chapter covers the industry best practices followed in enterprise Java applications.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Write clean JDBC code
- Improve database performance
- Prevent SQL Injection
- Handle resources properly
- Write maintainable applications
- Follow industry standards

---

# 1. Use PreparedStatement

Always prefer `PreparedStatement` over `Statement`.

✔ Secure

✔ Faster

✔ Prevents SQL Injection

Example:

```java
String sql =
    "SELECT * FROM students WHERE id=?";

PreparedStatement ps =
    connection.prepareStatement(sql);

ps.setInt(1, 101);
```

---

# 2. Use try-with-resources

Always close JDBC resources automatically.

```java
try (

    Connection connection =
        dataSource.getConnection();

    PreparedStatement ps =
        connection.prepareStatement(
            "SELECT * FROM students"
        );

    ResultSet rs =
        ps.executeQuery()

) {

    while (rs.next()) {

        System.out.println(
            rs.getString("name")
        );
    }
}
```

---

# 3. Never Hardcode Credentials

❌ Avoid:

```java
String user = "root";

String password = "password";
```

✔ Store credentials in:

- Properties files
- Environment variables
- Configuration servers
- Secret managers

---

# 4. Use Connection Pooling

Avoid creating a new connection for every request.

Use:

- HikariCP
- Apache DBCP
- C3P0

Connection pooling improves performance and scalability.

---

# 5. Handle Exceptions Properly

Always catch and log `SQLException`.

```java
catch (SQLException e) {

    e.printStackTrace();
}
```

Avoid empty catch blocks.

---

# 6. Close Resources

Always close:

- ResultSet
- Statement
- Connection

Or use try-with-resources to close them automatically.

---

# 7. Use Transactions

For multiple related operations:

```java
connection.setAutoCommit(false);

connection.commit();
```

If an error occurs:

```java
connection.rollback();
```

This keeps data consistent.

---

# 8. Validate User Input

Never trust user input.

Example:

```java
if (marks >= 0) {

    // Save record

}
```

Validation prevents invalid data from reaching the database.

---

# 9. Execute Batch Operations

For inserting or updating many records:

```java
ps.addBatch();

ps.executeBatch();
```

Batch processing improves performance.

---

# 10. Avoid Duplicate SQL

❌ Avoid writing the same SQL repeatedly.

✔ Create reusable methods or DAO classes.

Example:

```java
public Student findById(int id)
```

---

# 11. Use Meaningful Names

Good:

```java
studentStatement

studentConnection
```

Avoid:

```java
s1

c1

x
```

Readable code is easier to maintain.

---

# 12. Keep SQL Simple

Good:

```sql
SELECT *

FROM students

WHERE id=?
```

Avoid writing overly complex SQL when simpler queries achieve the same result.

---

# Recommended Project Structure

```text
src
│
├── config
├── dao
├── entity
├── service
├── util
└── Main.java
```

---

# JDBC Best Practice Workflow

```text
Read Configuration
        │
        ▼
Create Connection Pool
        │
        ▼
Get Connection
        │
        ▼
Use PreparedStatement
        │
        ▼
Execute SQL
        │
        ▼
Commit / Rollback
        │
        ▼
Close Resources
```

---

# Common Mistakes

### Using Statement

```java
Statement statement
```

Prefer:

```java
PreparedStatement
```

---

### Forgetting Transactions

Never execute multiple dependent operations without transaction management.

---

### Ignoring Exceptions

Never leave a catch block empty.

---

### Creating Connections Repeatedly

Use Connection Pooling instead.

---

# Real-World Practices

Enterprise applications typically use:

- DAO Pattern
- Connection Pooling
- Transactions
- Logging Frameworks
- Configuration Files
- PreparedStatement
- Layered Architecture

---

# Best Practices Checklist

| Practice | Recommended |
|----------|-------------|
| PreparedStatement | ✅ |
| try-with-resources | ✅ |
| Connection Pooling | ✅ |
| Transactions | ✅ |
| Input Validation | ✅ |
| Batch Processing | ✅ |
| Exception Logging | ✅ |
| Hardcoded Credentials | ❌ |
| Statement with User Input | ❌ |

---

# Summary

In this chapter, you learned:

- Secure JDBC coding
- Resource management
- Transactions
- Connection Pooling
- Batch Processing
- Exception handling
- Industry best practices

---

# Quick Revision

- Prefer `PreparedStatement`.
- Use try-with-resources.
- Avoid hardcoded credentials.
- Use Connection Pooling.
- Validate user input.
- Use transactions for related operations.
- Execute bulk operations using batch processing.
- Write reusable and maintainable code.

---

# Practice Questions

### Basic

1. Why is `PreparedStatement` preferred?
2. What is the advantage of try-with-resources?
3. Why should credentials not be hardcoded?
4. What is Connection Pooling?
5. Why should transactions be used?

### Intermediate

6. Explain the importance of batch processing.
7. How does input validation improve security?
8. Why is a layered project structure recommended?

### Interview Questions

1. What are the JDBC best practices followed in enterprise applications?
2. How can JDBC performance be improved?
3. Why is Connection Pooling preferred over creating new connections?
4. How would you secure a JDBC application?
5. Explain how you would structure a production-ready JDBC project.

---

# Hands-on Exercise

Create a **production-ready Student Management System** that:

1. Use `PreparedStatement` for all queries.
2. Configure HikariCP for Connection Pooling.
3. Store database credentials in a properties file.
4. Use try-with-resources throughout the project.
5. Implement transaction management for multiple database operations.
6. Perform bulk inserts using batch processing.
7. Log all SQL exceptions.
8. Organise the project using DAO, Service, Entity, Config, and Utility packages.
