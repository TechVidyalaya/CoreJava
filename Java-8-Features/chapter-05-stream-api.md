# Chapter 05: Stream API

## 📖 Overview

The **Stream API**, introduced in **Java 8**, provides a modern and efficient way to process collections. It supports operations such as filtering, sorting, mapping, reducing, and collecting data using a functional programming approach.

Streams help write cleaner, more readable, and more maintainable code.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Stream API
- Create Streams
- Perform intermediate and terminal operations
- Filter, map, sort, and collect data
- Use parallel streams
- Follow Stream API best practices

---

# What is a Stream?

A **Stream** is a sequence of elements that supports functional-style operations.

Unlike collections:

- Collections store data.
- Streams process data.

Example:

```java
List<String> names =
    Arrays.asList("Rahul", "Neha", "Amit");

names.stream()
     .forEach(System.out::println);
```

---

# Creating a Stream

From a Collection:

```java
List<Integer> numbers =
    Arrays.asList(10, 20, 30);

Stream<Integer> stream =
    numbers.stream();
```

From an Array:

```java
int[] nums = {10, 20, 30};

Arrays.stream(nums);
```

Using `Stream.of()`:

```java
Stream<String> stream =
    Stream.of("Java", "Spring", "SQL");
```

---

# Stream Pipeline

A Stream pipeline consists of three stages:

```
Source
   │
   ▼
Intermediate Operations
   │
   ▼
Terminal Operation
```

Example:

```java
numbers.stream()
       .filter(n -> n > 10)
       .map(n -> n * 2)
       .forEach(System.out::println);
```

---

# Intermediate Operations

Intermediate operations return another Stream.

Common operations:

| Method | Purpose |
|---------|---------|
| `filter()` | Select matching elements |
| `map()` | Transform elements |
| `sorted()` | Sort elements |
| `distinct()` | Remove duplicates |
| `limit()` | Restrict number of elements |
| `skip()` | Skip elements |

---

# filter()

Filters elements based on a condition.

```java
List<Integer> numbers =
    Arrays.asList(5, 10, 15, 20);

numbers.stream()
       .filter(n -> n > 10)
       .forEach(System.out::println);
```

Output

```
15
20
```

---

# map()

Transforms each element.

```java
List<String> names =
    Arrays.asList("java", "spring");

names.stream()
     .map(String::toUpperCase)
     .forEach(System.out::println);
```

Output

```
JAVA
SPRING
```

---

# sorted()

```java
List<Integer> numbers =
    Arrays.asList(30, 10, 20);

numbers.stream()
       .sorted()
       .forEach(System.out::println);
```

Output

```
10
20
30
```

Reverse order:

```java
numbers.stream()
       .sorted(Comparator.reverseOrder())
       .forEach(System.out::println);
```

---

# distinct()

Removes duplicate elements.

```java
Stream.of(1, 2, 2, 3, 3, 4)
      .distinct()
      .forEach(System.out::println);
```

Output

```
1
2
3
4
```

---

# limit() and skip()

```java
Stream.of(10, 20, 30, 40, 50)
      .limit(3)
      .forEach(System.out::println);
```

Output

```
10
20
30
```

```java
Stream.of(10, 20, 30, 40)
      .skip(2)
      .forEach(System.out::println);
```

Output

```
30
40
```

---

# Terminal Operations

Terminal operations produce the final result.

| Method | Purpose |
|---------|---------|
| `forEach()` | Iterate elements |
| `collect()` | Convert Stream to Collection |
| `count()` | Count elements |
| `findFirst()` | Get first element |
| `anyMatch()` | Check condition |
| `allMatch()` | Check all elements |
| `reduce()` | Produce a single result |

---

# collect()

```java
List<String> result =
    names.stream()
         .filter(name -> name.startsWith("R"))
         .collect(Collectors.toList());
```

---

# count()

```java
long count =
    numbers.stream()
           .count();

System.out.println(count);
```

---

# findFirst()

```java
Optional<Integer> first =
    numbers.stream()
           .findFirst();

System.out.println(first.get());
```

---

# anyMatch()

```java
boolean result =
    numbers.stream()
           .anyMatch(n -> n > 50);

System.out.println(result);
```

---

# reduce()

Calculate the sum.

```java
int sum =
    numbers.stream()
           .reduce(0, Integer::sum);

System.out.println(sum);
```

---

# Parallel Streams

Streams can execute tasks in parallel.

```java
numbers.parallelStream()
       .forEach(System.out::println);
```

Use parallel streams only when processing large datasets and independent operations.

---

# Stream vs Collection

| Collection | Stream |
|------------|--------|
| Stores data | Processes data |
| Reusable | Cannot be reused |
| Eager evaluation | Lazy evaluation |
| Supports add/remove | Read-only processing |

---

# Real-World Applications

Streams are commonly used in:

- Filtering employees
- Processing customer orders
- Data analytics
- Report generation
- REST API responses
- Spring Boot applications

---

# Common Mistakes

### Reusing a Stream

Incorrect:

```java
Stream<String> stream =
    names.stream();

stream.forEach(System.out::println);

stream.count();
```

Throws:

```
IllegalStateException
```

A Stream can be used only once.

---

### Forgetting Terminal Operation

```java
numbers.stream()
       .filter(n -> n > 10);
```

Nothing happens because no terminal operation is present.

---

### Using Parallel Streams Unnecessarily

Parallel Streams introduce overhead and may not improve performance for small datasets.

---

# Best Practices

- Prefer Streams for collection processing.
- Keep stream operations simple.
- Avoid modifying the source collection during stream processing.
- Use Method References where appropriate.
- Use Parallel Streams only after performance testing.

---

# Summary

In this chapter, you learned:

- Stream API
- Creating Streams
- Intermediate operations
- Terminal operations
- Parallel Streams
- Best practices

---

# Quick Revision

- Streams process data, not store it.
- A Stream consists of a source, intermediate operations, and a terminal operation.
- `filter()` selects elements.
- `map()` transforms elements.
- `collect()` converts a Stream into a collection.
- Streams cannot be reused.
- Parallel Streams execute operations concurrently.

---

# Practice Questions

### Basic

1. What is the Stream API?
2. How do you create a Stream?
3. What is the difference between intermediate and terminal operations?
4. What does `filter()` do?
5. What does `map()` do?

### Intermediate

6. Explain the Stream pipeline.
7. Compare Streams and Collections.
8. When should Parallel Streams be used?

### Interview Questions

1. What is lazy evaluation in Streams?
2. Why can't a Stream be reused?
3. Explain `filter()`, `map()`, and `reduce()` with examples.
4. What is the difference between `stream()` and `parallelStream()`?
5. Why are Streams preferred over traditional loops in modern Java?

---

# Hands-on Exercise

Create an **Employee Management** program that:

1. Create a list of employees.
2. Filter employees with a salary greater than ₹50,000.
3. Convert all employee names to uppercase.
4. Sort employees by salary.
5. Count the total number of employees.
6. Calculate the total salary using `reduce()`.
7. Store the filtered employees in a new list using `collect()`.
8. Compare the execution using `stream()` and `parallelStream()`.
