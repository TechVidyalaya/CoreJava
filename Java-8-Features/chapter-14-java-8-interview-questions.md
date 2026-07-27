# Chapter 14: Java 8 Interview Questions

## 📖 Overview

Java 8 is one of the most frequently tested topics in Java interviews. Interviewers often focus on **Lambda Expressions**, **Stream API**, **Optional**, **Functional Interfaces**, **Date & Time API**, and **CompletableFuture**.

This chapter covers the most commonly asked Java 8 interview questions with concise answers.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Prepare for Java 8 interviews
- Explain Java 8 features confidently
- Compare traditional Java with Java 8
- Answer practical coding questions
- Understand enterprise use cases

---

# Beginner Level Questions

## 1. What are the major features introduced in Java 8?

**Answer:**

- Lambda Expressions
- Functional Interfaces
- Method References
- Stream API
- Optional Class
- Date & Time API
- Default & Static Methods
- CompletableFuture
- Nashorn JavaScript Engine
- Base64 API

---

## 2. Why was Java 8 a major release?

**Answer:**

Java 8 introduced **functional programming** concepts, making Java code shorter, more readable, and better suited for parallel and asynchronous programming.

---

## 3. What is a Lambda Expression?

**Answer:**

A Lambda Expression is an anonymous function used to implement functional interfaces.

Example:

```java
(a, b) -> a + b
```

---

## 4. What is a Functional Interface?

**Answer:**

An interface containing exactly one abstract method.

Example:

```java
@FunctionalInterface
interface Calculator {

    int add(int a, int b);
}
```

---

## 5. What is a Method Reference?

**Answer:**

A shorter form of a lambda expression that refers to an existing method.

Example:

```java
System.out::println
```

---

# Intermediate Questions

## 6. What is the Stream API?

**Answer:**

The Stream API processes collections using operations such as:

- filter()
- map()
- sorted()
- collect()
- reduce()

It supports functional-style programming.

---

## 7. Difference between Collection and Stream?

| Collection | Stream |
|------------|--------|
| Stores data | Processes data |
| Reusable | Single use |
| Eager evaluation | Lazy evaluation |

---

## 8. What are Intermediate Operations?

Examples:

- filter()
- map()
- sorted()
- limit()
- skip()
- distinct()

These return another Stream.

---

## 9. What are Terminal Operations?

Examples:

- collect()
- forEach()
- count()
- reduce()
- findFirst()

These produce the final result.

---

## 10. Difference between map() and flatMap()?

### map()

Transforms each element individually.

### flatMap()

Flattens nested structures into a single stream.

---

## 11. What is Optional?

**Answer:**

Optional is a container that may or may not contain a value, helping avoid `NullPointerException`.

---

## 12. Difference between Optional.of() and Optional.ofNullable()?

| of() | ofNullable() |
|------|--------------|
| Doesn't allow null | Allows null |
| Throws NPE | Returns Optional.empty() |

---

## 13. What is the Java 8 Date & Time API?

**Answer:**

The `java.time` package provides immutable and thread-safe classes such as:

- LocalDate
- LocalTime
- LocalDateTime
- ZonedDateTime

---

## 14. What are Default Methods?

**Answer:**

Methods inside interfaces with an implementation.

They provide backward compatibility.

---

## 15. Can interfaces have static methods?

**Answer:**

Yes.

Example:

```java
interface MathUtil {

    static int square(int n) {

        return n * n;
    }
}
```

---

# Advanced Questions

## 16. What is CompletableFuture?

**Answer:**

A class used for asynchronous and non-blocking programming.

---

## 17. Difference between Future and CompletableFuture?

| Future | CompletableFuture |
|--------|-------------------|
| Limited features | Rich API |
| Blocking | Supports asynchronous chaining |
| No callbacks | Supports callbacks |

---

## 18. Difference between get() and join()?

| get() | join() |
|-------|--------|
| Checked exceptions | Unchecked exceptions |
| Requires try-catch | Cleaner syntax |

---

## 19. What is Lazy Evaluation?

**Answer:**

Intermediate Stream operations are executed only when a terminal operation is called.

---

## 20. What is Parallel Stream?

**Answer:**

A Stream that processes data using multiple threads.

Example:

```java
numbers.parallelStream();
```

---

## 21. What is reduce()?

**Answer:**

Produces a single result from multiple elements.

Example:

```java
int sum = numbers.stream()
                 .reduce(0, Integer::sum);
```

---

## 22. What is collect()?

**Answer:**

A terminal operation used to convert a Stream into a collection or another result.

---

## 23. Explain Collectors.groupingBy().

**Answer:**

Groups elements based on a key.

Example:

```java
employees.stream()

.collect(
Collectors.groupingBy(
Employee::getDepartment));
```

---

## 24. Difference between groupingBy() and partitioningBy()?

| groupingBy() | partitioningBy() |
|--------------|------------------|
| Multiple groups | Only two groups |
| Uses any key | Uses boolean condition |

---

## 25. Why can't Streams be reused?

**Answer:**

A Stream is consumed after a terminal operation.

Creating a new Stream is required for another operation.

---

# Scenario-Based Questions

## 26. How would you remove duplicates?

```java
stream.distinct();
```

---

## 27. How would you sort employees by salary?

```java
employees.stream()

.sorted(
Comparator.comparing(
Employee::getSalary));
```

---

## 28. How would you find the highest salary?

```java
employees.stream()

.max(
Comparator.comparing(
Employee::getSalary));
```

---

## 29. How would you convert names to uppercase?

```java
names.stream()

.map(String::toUpperCase);
```

---

## 30. How would you safely handle null values?

Use:

```java
Optional
```

instead of explicit null checks.

---

# Tips for Java 8 Interviews

- Understand concepts before memorising syntax.
- Practise writing Stream API code.
- Learn common Functional Interfaces.
- Know the difference between `map()` and `flatMap()`.
- Understand Optional usage.
- Practise asynchronous programming with `CompletableFuture`.
- Explain real-world use cases wherever possible.

---

# Summary

In this chapter, you learned:

- Common Java 8 interview questions
- Stream API interview concepts
- Optional interview topics
- CompletableFuture questions
- Functional programming concepts
- Enterprise interview tips

---

# Quick Revision

- Lambda Expressions simplify anonymous classes.
- Functional Interfaces contain one abstract method.
- Streams process collections.
- Optional helps avoid `NullPointerException`.
- CompletableFuture supports asynchronous programming.
- Default Methods improve interface evolution.
- Parallel Streams use multiple threads.

---

# Practice Questions

### Basic

1. What are the major features of Java 8?
2. What is a Lambda Expression?
3. What is a Functional Interface?
4. What is Optional?
5. What is the Stream API?

### Intermediate

6. Differentiate `map()` and `flatMap()`.
7. Explain `collect()` and `reduce()`.
8. Compare `Future` and `CompletableFuture`.

### Interview Questions

1. Why is Java 8 considered a revolutionary release?
2. Explain lazy evaluation in Streams.
3. When should Parallel Streams be avoided?
4. How does Optional reduce runtime errors?
5. What Java 8 features are most commonly used in Spring Boot applications?

---

# Hands-on Exercise

Create a **Java 8 Interview Practice** project that:

1. Demonstrates Lambda Expressions.
2. Uses all major Functional Interfaces.
3. Processes collections using the Stream API.
4. Performs grouping and partitioning using Collectors.
5. Handles null values using Optional.
6. Formats dates using the Date & Time API.
7. Executes asynchronous tasks with CompletableFuture.
8. Prepare explanations for each implementation as if answering an interview question.
