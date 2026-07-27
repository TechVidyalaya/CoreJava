# Chapter 07: Optional Class

## 📖 Overview

The **Optional** class was introduced in **Java 8** to reduce the chances of `NullPointerException` (NPE). It acts as a container that may or may not contain a non-null value, encouraging developers to explicitly handle missing values.

`Optional` is widely used in modern Java applications, especially in **Spring Boot**, **REST APIs**, and **Repository** methods.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Optional class
- Create Optional objects
- Check and retrieve values safely
- Use common Optional methods
- Avoid `NullPointerException`
- Follow Optional best practices

---

# What is Optional?

`Optional<T>` is a container object that may contain a value or be empty.

Instead of:

```java
String name = null;

System.out.println(name.length());
```

Output

```
NullPointerException
```

Use:

```java
Optional<String> name =
    Optional.ofNullable(null);
```

---

# Creating an Optional

## Optional.of()

Creates an Optional containing a non-null value.

```java
Optional<String> name =
    Optional.of("Java");

System.out.println(name);
```

Output

```
Optional[Java]
```

> `Optional.of()` throws `NullPointerException` if the value is `null`.

---

## Optional.ofNullable()

Accepts both null and non-null values.

```java
Optional<String> name =
    Optional.ofNullable(null);

System.out.println(name);
```

Output

```
Optional.empty
```

---

## Optional.empty()

Creates an empty Optional.

```java
Optional<String> name =
    Optional.empty();
```

---

# Checking if a Value Exists

## isPresent()

```java
Optional<String> name =
    Optional.of("Rahul");

System.out.println(name.isPresent());
```

Output

```
true
```

---

## isEmpty() (Java 11+)

```java
Optional<String> name =
    Optional.empty();

System.out.println(name.isEmpty());
```

Output

```
true
```

---

# Retrieving Values

## get()

```java
Optional<String> name =
    Optional.of("Java");

System.out.println(name.get());
```

Output

```
Java
```

> Avoid calling `get()` without checking if a value exists.

---

# Providing Default Values

## orElse()

```java
Optional<String> name =
    Optional.empty();

System.out.println(
    name.orElse("Guest")
);
```

Output

```
Guest
```

---

## orElseGet()

Computes a default value only when needed.

```java
String result =
    name.orElseGet(() -> "Default User");
```

---

## orElseThrow()

Throws an exception if the value is absent.

```java
String value =
    name.orElseThrow(
        () -> new RuntimeException("Name not found")
    );
```

---

# Executing Code if Present

## ifPresent()

```java
Optional<String> name =
    Optional.of("Java");

name.ifPresent(
    System.out::println
);
```

Output

```
Java
```

---

# Transforming Values

## map()

```java
Optional<String> name =
    Optional.of("java");

Optional<String> upper =
    name.map(String::toUpperCase);

System.out.println(upper.get());
```

Output

```
JAVA
```

---

## filter()

```java
Optional<String> name =
    Optional.of("Rahul");

Optional<String> result =
    name.filter(
        n -> n.startsWith("R")
    );

System.out.println(result.isPresent());
```

Output

```
true
```

---

# Common Optional Methods

| Method | Purpose |
|---------|---------|
| `of()` | Create Optional with non-null value |
| `ofNullable()` | Accept null or non-null |
| `empty()` | Create empty Optional |
| `isPresent()` | Check if value exists |
| `get()` | Retrieve value |
| `orElse()` | Return default value |
| `orElseGet()` | Lazily create default value |
| `orElseThrow()` | Throw exception if empty |
| `ifPresent()` | Execute action if value exists |
| `map()` | Transform value |
| `filter()` | Apply condition |

---

# Optional Workflow

```
Value
  │
  ▼
Optional
  │
  ├── Present
  │      │
  │      ▼
  │   Process Value
  │
  └── Empty
         │
         ▼
   Default / Exception
```

---

# Real-World Applications

Optional is commonly used in:

- Spring Data JPA `findById()`
- REST API responses
- Configuration values
- User profile lookup
- Database queries
- Cache retrieval

Example:

```java
Optional<Employee> employee =
    repository.findById(101);
```

---

# Common Mistakes

### Using Optional.of() with Null

Incorrect:

```java
Optional.of(null);
```

Throws:

```
NullPointerException
```

Use:

```java
Optional.ofNullable(null);
```

---

### Calling get() Directly

Incorrect:

```java
name.get();
```

If empty:

```
NoSuchElementException
```

Prefer:

```java
name.orElse("Guest");
```

---

### Using Optional as a Field

```java
class Employee {

    Optional<String> name;
}
```

Generally avoid using `Optional` as a class field or method parameter. It is primarily intended for **return types**.

---

# Best Practices

- Use `Optional` as a return type.
- Prefer `orElse()` or `orElseGet()` over `get()`.
- Use `ofNullable()` when a value may be null.
- Keep Optional chains simple and readable.
- Avoid storing Optional in entity fields.

---

# Summary

In this chapter, you learned:

- Optional class
- Creating Optional objects
- Retrieving values safely
- Default values
- Mapping and filtering
- Best practices

---

# Quick Revision

- `Optional` helps avoid `NullPointerException`.
- `of()` requires a non-null value.
- `ofNullable()` accepts null values.
- `orElse()` returns a default value.
- `ifPresent()` executes code only when a value exists.
- `map()` transforms the contained value.

---

# Practice Questions

### Basic

1. What is the purpose of the Optional class?
2. What is the difference between `of()` and `ofNullable()`?
3. What does `isPresent()` return?
4. What is `Optional.empty()`?
5. Which method returns a default value?

### Intermediate

6. Differentiate `orElse()` and `orElseGet()`.
7. Explain `map()` and `filter()` with examples.
8. Why is `Optional` preferred over null checks?

### Interview Questions

1. Why was Optional introduced in Java 8?
2. When should `Optional` be used?
3. Why should `get()` generally be avoided?
4. What is the difference between `orElse()`, `orElseGet()`, and `orElseThrow()`?
5. Why is using Optional as an entity field considered a bad practice?

---

# Hands-on Exercise

Create a **Student Management** program that:

1. Create a `Student` class with:
   - ID
   - Name
   - Email
2. Create a method that returns `Optional<Student>`.
3. Search for a student by ID.
4. If found:
   - Print the student details.
5. If not found:
   - Display `"Student Not Found"` using `orElse()`.
6. Convert the student's name to uppercase using `map()`.
7. Use `ifPresent()` to print the student's email.
8. Handle missing data without using explicit null checks.
