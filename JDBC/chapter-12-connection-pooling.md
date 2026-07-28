# Chapter 12: Connection Pooling

## 📖 Overview

Creating a new database connection for every request is expensive and slows down applications. **Connection Pooling** improves performance by maintaining a pool of reusable database connections.

Modern Java applications commonly use connection pools such as **HikariCP**, **Apache DBCP**, and **C3P0**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Connection Pooling
- Learn why it is needed
- Configure HikariCP
- Obtain and release connections
- Improve application performance
- Follow best practices

---

# What is Connection Pooling?

Connection Pooling is a technique where database connections are created once and reused multiple times.

Instead of creating a new connection for every request, the application borrows one from the pool and returns it after use.

---

# Without Connection Pooling

```text
Request
   │
   ▼
Create Connection
   │
   ▼
Execute Query
   │
   ▼
Close Connection
```

A new connection is created for every request.

---

# With Connection Pooling

```text
Request
   │
   ▼
Connection Pool
   │
   ▼
Borrow Connection
   │
   ▼
Execute Query
   │
   ▼
Return Connection
```

Connections are reused, improving performance.

---

# Benefits of Connection Pooling

- Faster database access
- Reduced connection creation time
- Better application performance
- Efficient resource utilisation
- Improved scalability

---

# Popular Connection Pool Libraries

| Library | Description |
|----------|-------------|
| HikariCP | Fast and lightweight (Most Popular) |
| Apache DBCP | Apache connection pool |
| C3P0 | Mature connection pool library |

---

# HikariCP Maven Dependency

```xml
<dependency>
    <groupId>com.zaxxer</groupId>
    <artifactId>HikariCP</artifactId>
    <version>6.3.0</version>
</dependency>
```

---

# Creating a Connection Pool

```java
HikariConfig config =
    new HikariConfig();

config.setJdbcUrl(
    "jdbc:mysql://localhost:3306/student_db"
);

config.setUsername("root");
config.setPassword("password");

HikariDataSource dataSource =
    new HikariDataSource(config);
```

---

# Getting a Connection

```java
Connection connection =
    dataSource.getConnection();
```

---

# Returning a Connection

```java
connection.close();
```

> **Note:** Calling `close()` does **not** destroy the connection. It returns the connection to the pool for reuse.

---

# Using try-with-resources

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

# Important Configuration Options

| Method | Purpose |
|---------|---------|
| `setMaximumPoolSize()` | Maximum connections |
| `setMinimumIdle()` | Minimum idle connections |
| `setConnectionTimeout()` | Wait time for a connection |
| `setIdleTimeout()` | Idle connection timeout |
| `setMaxLifetime()` | Maximum connection lifetime |

Example:

```java
config.setMaximumPoolSize(10);

config.setMinimumIdle(2);
```

---

# Connection Pool Lifecycle

```text
Application Starts
        │
        ▼
Create Connection Pool
        │
        ▼
Borrow Connection
        │
        ▼
Execute Query
        │
        ▼
Return Connection
        │
        ▼
Reuse Connection
```

---

# Connection Pooling vs Normal JDBC

| Feature | Normal JDBC | Connection Pool |
|---------|-------------|-----------------|
| Connection Creation | Every request | One-time creation |
| Performance | Lower | Higher |
| Scalability | Limited | Excellent |
| Resource Usage | High | Optimised |

---

# Real-World Applications

Connection Pooling is used in:

- Spring Boot applications
- Banking systems
- E-commerce websites
- REST APIs
- Microservices
- Enterprise applications

---

# Common Mistakes

### Creating Multiple Pools

Incorrect:

```java
new HikariDataSource(config);
```

Create the pool once and reuse it.

---

### Not Closing Connections

Incorrect:

```java
Connection connection =
    dataSource.getConnection();
```

Always close the connection after use.

```java
connection.close();
```

This returns it to the pool.

---

### Very Large Pool Size

Setting an unnecessarily large pool wastes database resources.

Choose the pool size based on application load and database capacity.

---

# Best Practices

- Prefer **HikariCP** for modern Java applications.
- Create a single connection pool per application.
- Always use try-with-resources.
- Close connections after use.
- Configure pool size appropriately.
- Monitor connection pool usage in production.

---

# Summary

In this chapter, you learned:

- Connection Pooling
- Benefits
- HikariCP
- Pool configuration
- Borrowing and returning connections
- Best practices

---

# Quick Revision

- Connection Pooling reuses database connections.
- HikariCP is the most popular connection pool library.
- `getConnection()` borrows a connection.
- `close()` returns the connection to the pool.
- Configure the pool based on application needs.
- Use try-with-resources.
- Connection Pooling improves performance and scalability.

---

# Practice Questions

### Basic

1. What is Connection Pooling?
2. Why is Connection Pooling faster?
3. Name two Connection Pool libraries.
4. Which library is most commonly used today?
5. What happens when `connection.close()` is called on a pooled connection?

### Intermediate

6. Explain how HikariCP works.
7. Why should only one connection pool be created?
8. What factors affect the ideal pool size?

### Interview Questions

1. Explain Connection Pooling in JDBC.
2. Why is HikariCP preferred over creating connections manually?
3. What is the difference between closing a pooled connection and a normal JDBC connection?
4. What are the important HikariCP configuration properties?
5. How does Connection Pooling improve application performance?

---

# Hands-on Exercise

Create a **Student Management** application using **HikariCP** that:

1. Add the HikariCP dependency.
2. Configure a connection pool for the `student_db` database.
3. Retrieve a connection from the pool.
4. Display all student records.
5. Insert a new student record.
6. Update a student's marks.
7. Return the connection to the pool using `close()`.
8. Compare the performance of pooled connections with normal JDBC connections.
