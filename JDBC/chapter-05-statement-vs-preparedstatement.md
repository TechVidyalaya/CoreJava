# Chapter 05: Statement vs PreparedStatement

## 📖 Overview

JDBC provides two commonly used interfaces for executing SQL statements:

- **Statement**
- **PreparedStatement**

Although both execute SQL queries, **PreparedStatement** is preferred in real-world applications because it is **faster, more secure, and prevents SQL Injection attacks**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand `Statement`
- Understand `PreparedStatement`
- Compare both interfaces
- Prevent SQL Injection
- Choose the appropriate interface
- Follow JDBC best practices

---

# What is Statement?

A `Statement` executes static SQL queries.

Example:

```java
Statement statement =
    connection.createStatement();
```

Execute a query:

```java
ResultSet rs =
    statement.executeQuery(
        "SELECT * FROM students"
    );
```

---

# What is PreparedStatement?

A `PreparedStatement` executes **parameterized SQL queries**.

Example:

```java
PreparedStatement ps =
    connection.prepareStatement(
        "SELECT * FROM students WHERE id = ?"
    );
```

Set parameter:

```java
ps.setInt(1, 101);
```

Execute:

```java
ResultSet rs =
    ps.executeQuery();
```

---

# Statement Example

```java
String sql =
    "SELECT * FROM students WHERE id = 101";

Statement statement =
    connection.createStatement();

ResultSet rs =
    statement.executeQuery(sql);
```

---

# PreparedStatement Example

```java
String sql =
    "SELECT * FROM students WHERE id = ?";

PreparedStatement ps =
    connection.prepareStatement(sql);

ps.setInt(1, 101);

ResultSet rs =
    ps.executeQuery();
```

---

# SQL Injection

SQL Injection occurs when user input changes the SQL query.

Unsafe Example:

```java
String sql =
    "SELECT * FROM users WHERE username='"
    + username +
    "' AND password='"
    + password + "'";
```

If malicious input is provided, attackers may gain unauthorized access.

---

# Preventing SQL Injection

Use `PreparedStatement`.

```java
String sql =
    "SELECT * FROM users WHERE username=? AND password=?";

PreparedStatement ps =
    connection.prepareStatement(sql);

ps.setString(1, username);

ps.setString(2, password);
```

The JDBC driver treats user input as data, not executable SQL.

---

# Executing INSERT

Using `PreparedStatement`:

```java
String sql =
    "INSERT INTO students VALUES (?, ?, ?, ?)";

PreparedStatement ps =
    connection.prepareStatement(sql);

ps.setInt(1, 101);
ps.setString(2, "Rahul");
ps.setString(3, "Java");
ps.setInt(4, 90);

ps.executeUpdate();
```

---

# Executing UPDATE

```java
String sql =
    "UPDATE students SET marks=? WHERE id=?";

PreparedStatement ps =
    connection.prepareStatement(sql);

ps.setInt(1, 95);
ps.setInt(2, 101);

ps.executeUpdate();
```

---

# Executing DELETE

```java
String sql =
    "DELETE FROM students WHERE id=?";

PreparedStatement ps =
    connection.prepareStatement(sql);

ps.setInt(1, 101);

ps.executeUpdate();
```

---

# Statement vs PreparedStatement

| Feature | Statement | PreparedStatement |
|---------|-----------|-------------------|
| Query Type | Static | Parameterized |
| Performance | Slower | Faster (Reusable) |
| SQL Injection | Vulnerable | Protected |
| Parameter Support | No | Yes |
| Recommended | No | Yes |

---

# When to Use?

Use **Statement** when:

- Executing simple static SQL
- No user input is involved

Use **PreparedStatement** when:

- Taking user input
- Executing repeated queries
- Building enterprise applications

---

# Workflow

```text
User Input
      │
      ▼
PreparedStatement
      │
      ▼
Set Parameters
      │
      ▼
Execute SQL
      │
      ▼
Database
      │
      ▼
Result
```

---

# Real-World Applications

`PreparedStatement` is widely used in:

- Login systems
- Registration forms
- Banking applications
- Student Management Systems
- E-commerce platforms
- Spring Boot applications

---

# Common Mistakes

### Using Statement with User Input

Avoid:

```java
Statement
```

It increases the risk of SQL Injection.

---

### Forgetting Parameters

Incorrect:

```java
PreparedStatement ps =
    connection.prepareStatement(sql);

ps.executeQuery();
```

Always set all required parameters before execution.

---

### Wrong Parameter Index

Indexes start from **1**, not **0**.

Correct:

```java
ps.setString(1, "Java");
```

---

# Best Practices

- Prefer `PreparedStatement` over `Statement`.
- Never concatenate user input into SQL queries.
- Reuse `PreparedStatement` for repeated executions.
- Validate user input where appropriate.
- Close statements after use.
- Use try-with-resources for automatic cleanup.

---

# Summary

In this chapter, you learned:

- Statement
- PreparedStatement
- SQL Injection
- Parameterized queries
- CRUD using PreparedStatement
- Best practices

---

# Quick Revision

- `Statement` executes static SQL.
- `PreparedStatement` executes parameterized SQL.
- `PreparedStatement` prevents SQL Injection.
- Parameters are represented using `?`.
- Parameter indexes start from **1**.
- `executeQuery()` is used for `SELECT`.
- `executeUpdate()` is used for `INSERT`, `UPDATE`, and `DELETE`.

---

# Practice Questions

### Basic

1. What is a `Statement`?
2. What is a `PreparedStatement`?
3. What is SQL Injection?
4. Which interface is more secure?
5. What does `executeUpdate()` return?

### Intermediate

6. Differentiate `Statement` and `PreparedStatement`.
7. Why is `PreparedStatement` faster for repeated queries?
8. How does `PreparedStatement` prevent SQL Injection?

### Interview Questions

1. Explain the difference between `Statement` and `PreparedStatement`.
2. Why is `PreparedStatement` preferred in enterprise applications?
3. What is SQL Injection? How can it be prevented?
4. When would you use `Statement` instead of `PreparedStatement`?
5. Explain the role of parameter placeholders (`?`) in JDBC.

---

# Hands-on Exercise

Create a **Student Management** application that:

1. Create a `students` table in `student_db`.
2. Insert student records using `PreparedStatement`.
3. Search for a student using the student ID.
4. Update a student's marks.
5. Delete a student record.
6. Demonstrate how SQL Injection can occur with `Statement`.
7. Prevent the attack by replacing `Statement` with `PreparedStatement`.
8. Compare the performance and security of both approaches.
