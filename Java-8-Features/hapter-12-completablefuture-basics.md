# Chapter 12: CompletableFuture Basics

## 📖 Overview

`CompletableFuture` is a powerful feature introduced in **Java 8** for writing **asynchronous** and **non-blocking** programs. It allows tasks to run in the background, combine multiple tasks, handle exceptions, and improve application performance.

It is widely used in **Spring Boot**, **Microservices**, **REST APIs**, and **high-performance enterprise applications**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand asynchronous programming
- Create and use CompletableFuture
- Run tasks asynchronously
- Combine multiple tasks
- Handle exceptions
- Follow CompletableFuture best practices

---

# What is CompletableFuture?

A `CompletableFuture` represents the result of an asynchronous computation that may complete in the future.

Instead of waiting for a task to finish, the program can continue executing other work.

```
Start Task
    │
    ▼
Runs in Background
    │
    ▼
Task Completes
    │
    ▼
Result Available
```

---

# Why CompletableFuture?

Without asynchronous programming:

- Program waits for each task
- Resources remain idle
- Lower performance

With CompletableFuture:

- Multiple tasks execute simultaneously
- Better CPU utilization
- Faster response time

---

# Creating a CompletableFuture

```java
import java.util.concurrent.CompletableFuture;

CompletableFuture<String> future =
    CompletableFuture.completedFuture("Hello");

System.out.println(future.get());
```

Output

```
Hello
```

---

# Running a Task Asynchronously

```java
CompletableFuture.runAsync(() -> {

    System.out.println("Running Task...");
});
```

`runAsync()` is used when no result needs to be returned.

---

# Returning a Value

```java
CompletableFuture<String> future =
    CompletableFuture.supplyAsync(() -> {

        return "Java 8";
    });

System.out.println(future.get());
```

Output

```
Java 8
```

---

# Processing the Result

```java
CompletableFuture.supplyAsync(() -> "Java")

    .thenApply(String::toUpperCase)

    .thenAccept(System.out::println);
```

Output

```
JAVA
```

---

# Chaining Tasks

```java
CompletableFuture.supplyAsync(() -> 10)

    .thenApply(n -> n * 2)

    .thenApply(n -> n + 5)

    .thenAccept(System.out::println);
```

Output

```
25
```

---

# Combining Two Futures

```java
CompletableFuture<Integer> future1 =
    CompletableFuture.supplyAsync(() -> 20);

CompletableFuture<Integer> future2 =
    CompletableFuture.supplyAsync(() -> 30);

future1.thenCombine(future2,
    Integer::sum)

    .thenAccept(System.out::println);
```

Output

```
50
```

---

# Waiting for Multiple Tasks

```java
CompletableFuture<Void> all =
    CompletableFuture.allOf(
        future1,
        future2
    );

all.join();
```

`allOf()` waits until all tasks are complete.

---

# Waiting for Any Task

```java
CompletableFuture<Object> any =
    CompletableFuture.anyOf(
        future1,
        future2
    );

System.out.println(any.join());
```

`anyOf()` returns the result of the first completed task.

---

# Exception Handling

```java
CompletableFuture<Integer> future =
    CompletableFuture.supplyAsync(() -> {

        return 10 / 0;
    })

    .exceptionally(ex -> {

        System.out.println(ex.getMessage());

        return 0;
    });

System.out.println(future.join());
```

Output

```
/ by zero
0
```

---

# Common Methods

| Method | Purpose |
|---------|---------|
| `runAsync()` | Run task without result |
| `supplyAsync()` | Run task with result |
| `thenApply()` | Transform result |
| `thenAccept()` | Consume result |
| `thenRun()` | Execute another task |
| `thenCombine()` | Combine two futures |
| `allOf()` | Wait for all tasks |
| `anyOf()` | Wait for first completed task |
| `exceptionally()` | Handle exceptions |
| `join()` | Wait without checked exception |
| `get()` | Wait with checked exception |

---

# get() vs join()

| `get()` | `join()` |
|-----------|----------|
| Throws checked exceptions | Throws unchecked exceptions |
| Requires try-catch | Simpler syntax |
| Older Future style | Preferred with CompletableFuture |

---

# Real-World Applications

CompletableFuture is widely used in:

- Calling multiple REST APIs
- Database operations
- Email notifications
- File processing
- Microservices
- Spring Boot applications

Example:

```
User Request
     │
     ├── Fetch User
     ├── Fetch Orders
     ├── Fetch Payments
     │
     ▼
Combine Results
     │
     ▼
Return Response
```

---

# Common Mistakes

### Calling get() Immediately

```java
CompletableFuture<String> future =
    CompletableFuture.supplyAsync(() -> "Java");

future.get();
```

Calling `get()` immediately blocks the current thread, reducing the benefit of asynchronous execution.

---

### Ignoring Exceptions

Always handle exceptions using:

```java
.exceptionally(...)
```

or

```java
.handle(...)
```

---

### Using Too Many Nested Futures

Avoid deeply nested callbacks.

Prefer chaining methods such as:

```java
thenApply()

thenCompose()

thenCombine()
```

---

# Best Practices

- Prefer `supplyAsync()` when a result is needed.
- Use `runAsync()` for background tasks without results.
- Use `join()` when checked exceptions are unnecessary.
- Handle exceptions gracefully.
- Keep asynchronous tasks independent whenever possible.
- Use custom thread pools for production applications instead of relying solely on the common pool.

---

# Summary

In this chapter, you learned:

- CompletableFuture
- Asynchronous programming
- `runAsync()` and `supplyAsync()`
- Chaining operations
- Combining multiple futures
- Exception handling
- Best practices

---

# Quick Revision

- `CompletableFuture` enables asynchronous programming.
- `runAsync()` executes tasks without returning a value.
- `supplyAsync()` returns a result.
- `thenApply()` transforms results.
- `thenCombine()` combines multiple tasks.
- `allOf()` waits for all tasks.
- `exceptionally()` handles errors.
- `join()` is commonly preferred over `get()`.

---

# Practice Questions

### Basic

1. What is `CompletableFuture`?
2. What is asynchronous programming?
3. What is the difference between `runAsync()` and `supplyAsync()`?
4. What does `thenApply()` do?
5. What is the purpose of `allOf()`?

### Intermediate

6. Differentiate `get()` and `join()`.
7. Explain `thenCombine()` with an example.
8. How do you handle exceptions in `CompletableFuture`?

### Interview Questions

1. Why was `CompletableFuture` introduced in Java 8?
2. How is `CompletableFuture` different from `Future`?
3. Explain `thenApply()`, `thenCompose()`, and `thenCombine()`.
4. When should `allOf()` and `anyOf()` be used?
5. What are the best practices for asynchronous programming in Java?

---

# Hands-on Exercise

Create an **Online Shopping Dashboard** that:

1. Fetch user details asynchronously.
2. Fetch order history asynchronously.
3. Fetch payment information asynchronously.
4. Fetch product recommendations asynchronously.
5. Wait for all tasks using `allOf()`.
6. Combine the results into a single response.
7. Handle failures using `exceptionally()`.
8. Display the final dashboard once all background tasks are completed.
