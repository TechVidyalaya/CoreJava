# Chapter 11: JDBC Exception Handling

## 📖 Overview

Database operations may fail due to reasons such as invalid SQL, connection issues, missing tables, or incorrect data. JDBC provides a robust exception handling mechanism to detect and handle these errors gracefully.

Proper exception handling makes applications more reliable and easier to debug.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand JDBC exceptions
- Handle SQL exceptions
- Read exception details
- Use try-with-resources
- Write robust JDBC programs
- Follow exception handling best practices

---

# What is SQLException?

`SQLException` is the primary exception class used for database-related errors.

Common causes:

- Invalid SQL query
- Database connection failure
- Incorrect table name
- Constraint violations
- Network issues

---

# Basic Exception Handling

```java
try {

    Connection connection =
        DriverManager.getConnection(
            url,
            user,
            password
        );

}
catch (SQLException e) {

    System.out.println(
        e.getMessage()
    );
}
```

---

# Common SQLException Methods

| Method | Purpose |
|---------|---------|
| `getMessage()` | Error message |
| `getErrorCode()` | Database error code |
| `getSQLState()` | SQL state code |
| `printStackTrace()` | Prints complete error details |

---

# Reading Exception Details

```java
catch (SQLException e) {

    System.out.println(
        e.getMessage()
    );

    System.out.println(
        e.getErrorCode()
    );

    System.out.println(
        e.getSQLState()
    );
}
```

---

# Using try-with-resources

Instead of manually closing resources:

```java
try (

    Connection connection =
        DriverManager.getConnection(url, user, password);

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
catch (SQLException e) {

    e.printStackTrace();
}
```

Resources are closed automatically.

---

# Handling Multiple Exceptions

```java
try {

    int number = 10 / 0;

}
catch (ArithmeticException e) {

    System.out.println("Math Error");

}
catch (SQLException e) {

    System.out.println("Database Error");

}
```

---

# Finally Block

The `finally` block executes whether an exception occurs or not.

```java
Connection connection = null;

try {

    connection =
        DriverManager.getConnection(
            url,
            user,
            password
        );

}
catch (SQLException e) {

    e.printStackTrace();

}
finally {

    System.out.println(
        "Resources Closed"
    );
}
```

> With try-with-resources, a `finally` block is usually unnecessary for closing JDBC resources.

---

# Common JDBC Exceptions

| Exception | Cause |
|-----------|-------|
| `SQLException` | Database error |
| `SQLSyntaxErrorException` | Invalid SQL syntax |
| `SQLIntegrityConstraintViolationException` | Duplicate key or constraint violation |
| `BatchUpdateException` | Batch execution failure |
| `SQLTimeoutException` | Query execution timeout |

---

# Exception Handling Workflow

```text
Execute SQL
      │
      ▼
Exception Occurred?
      │
 ┌────┴────┐
 │         │
No        Yes
 │         │
 ▼         ▼
Continue  Catch Exception
              │
              ▼
       Log / Display Error
              │
              ▼
      Close Resources
```

---

# Logging Exceptions

Instead of ignoring exceptions:

```java
catch (SQLException e) {

    e.printStackTrace();
}
```

In enterprise applications, use logging frameworks such as Log4j or SLF4J instead of `printStackTrace()`.

---

# Real-World Applications

Exception handling is essential in:

- Banking systems
- E-commerce applications
- Hospital Management Systems
- ERP software
- Student portals
- Financial applications

---

# Common Mistakes

### Empty Catch Block

Incorrect:

```java
catch (SQLException e) {

}
```

Always log or handle the exception.

---

### Ignoring Resource Closure

Always use:

```java
try-with-resources
```

instead of manually closing resources.

---

### Showing Internal Errors to Users

Avoid displaying database errors directly to end users.

Instead:

- Log detailed errors
- Show a user-friendly message

---

# Best Practices

- Always catch `SQLException`.
- Prefer try-with-resources.
- Log exceptions for debugging.
- Avoid empty catch blocks.
- Do not expose database details to users.
- Handle exceptions at the appropriate level.

---

# Summary

In this chapter, you learned:

- SQLException
- Exception handling
- try-with-resources
- Common JDBC exceptions
- Logging
- Best practices

---

# Quick Revision

- `SQLException` handles database errors.
- `getMessage()` returns the error description.
- `getErrorCode()` returns the database-specific code.
- `getSQLState()` returns the SQL state.
- Prefer try-with-resources.
- Log exceptions instead of ignoring them.
- Do not expose technical error details to users.

---

# Practice Questions

### Basic

1. What is `SQLException`?
2. Which method returns the exception message?
3. Why is try-with-resources preferred?
4. What is the purpose of `finally`?
5. Which exception occurs for invalid SQL syntax?

### Intermediate

6. Explain the advantages of try-with-resources.
7. How do you retrieve the SQL state of an exception?
8. Why should exceptions be logged?

### Interview Questions

1. Explain exception handling in JDBC.
2. What is the difference between `getMessage()` and `getErrorCode()`?
3. Why is try-with-resources recommended?
4. How would you handle database failures in an enterprise application?
5. What are the common JDBC exceptions?

---

# Hands-on Exercise

Create a **Student Management** application that:

1. Connect to the database.
2. Execute valid and invalid SQL queries.
3. Handle all database exceptions using `try-catch`.
4. Display the exception message, SQL state, and error code.
5. Replace manual resource closing with try-with-resources.
6. Log errors appropriately.
7. Show a user-friendly message when an error occurs.
8. Verify that all resources are closed automatically.
