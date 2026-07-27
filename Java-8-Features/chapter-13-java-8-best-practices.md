# Chapter 13: Java 8 Best Practices

## 📖 Overview

Java 8 introduced powerful features such as **Lambda Expressions**, **Streams**, **Optional**, **CompletableFuture**, and the **Date & Time API**. While these features make code concise and expressive, using them incorrectly can reduce readability and performance.

This chapter covers the best practices followed by experienced Java developers when writing Java 8 applications.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Write clean Java 8 code
- Use Streams efficiently
- Avoid common Optional mistakes
- Write better Lambda expressions
- Improve performance
- Follow enterprise coding standards

---

# 1. Prefer Lambda Expressions

Instead of anonymous classes:

```java
Runnable task = new Runnable() {

    @Override
    public void run() {

        System.out.println("Running");
    }
};
```

Use:

```java
Runnable task =
    () -> System.out.println("Running");
```

✔ Cleaner

✔ Easier to read

✔ Less boilerplate

---

# 2. Use Method References

Instead of:

```java
names.forEach(name ->
    System.out.println(name));
```

Use:

```java
names.forEach(System.out::println);
```

Method references improve readability.

---

# 3. Keep Lambdas Short

Good:

```java
numbers.stream()
       .filter(n -> n > 10);
```

Avoid:

```java
numbers.stream()
       .filter(n -> {

           // many lines of code

           return true;
       });
```

Move complex logic into separate methods.

---

# 4. Use Streams for Collection Processing

Instead of:

```java
for(String name : names){

    if(name.startsWith("A")){

        System.out.println(name);
    }
}
```

Use:

```java
names.stream()

     .filter(name ->
         name.startsWith("A"))

     .forEach(System.out::println);
```

---

# 5. Avoid Reusing Streams

Incorrect:

```java
Stream<String> stream =
    names.stream();

stream.count();

stream.forEach(System.out::println);
```

This throws:

```
IllegalStateException
```

Create a new Stream whenever needed.

---

# 6. Avoid Side Effects in Streams

Incorrect:

```java
List<String> result =
    new ArrayList<>();

names.stream()
     .forEach(result::add);
```

Better:

```java
List<String> result =
    names.stream()
         .collect(Collectors.toList());
```

---

# 7. Use Optional Properly

Incorrect:

```java
Optional<String> name =
    Optional.of(null);
```

Correct:

```java
Optional<String> name =
    Optional.ofNullable(null);
```

---

# 8. Avoid Calling get()

Instead of:

```java
name.get();
```

Use:

```java
name.orElse("Guest");
```

or

```java
name.orElseThrow();
```

---

# 9. Use Date & Time API

Avoid:

```java
Date date = new Date();
```

Prefer:

```java
LocalDate.now();

LocalDateTime.now();
```

The Java 8 API is immutable and thread-safe.

---

# 10. Handle Exceptions in CompletableFuture

```java
CompletableFuture.supplyAsync(() -> {

    return calculate();

})

.exceptionally(ex -> {

    return 0;
});
```

Always provide exception handling for asynchronous tasks.

---

# 11. Use Parallel Streams Carefully

Suitable for:

- Large datasets
- CPU-intensive operations
- Independent tasks

Avoid using parallel streams for:

- Small collections
- I/O operations
- Shared mutable data

---

# 12. Prefer Immutable Objects

Good:

```java
LocalDate today =
    LocalDate.now();
```

Avoid modifying shared mutable objects inside streams or lambdas.

---

# 13. Use Functional Interfaces

Instead of creating custom interfaces unnecessarily, prefer built-in interfaces.

```java
Predicate<String>

Function<String, Integer>

Consumer<String>

Supplier<String>
```

---

# 14. Keep Stream Pipelines Readable

Good:

```java
employees.stream()

         .filter(Employee::isActive)

         .sorted(
             Comparator.comparing(
                 Employee::getSalary))

         .collect(Collectors.toList());
```

Avoid long, deeply nested pipelines.

---

# 15. Write Clean Code

- Use meaningful variable names.
- Keep methods small.
- Avoid duplicate logic.
- Prefer readability over clever code.

---

# Performance Tips

| Practice | Benefit |
|----------|---------|
| Use Streams for collections | Cleaner code |
| Use Method References | Better readability |
| Use Optional | Avoid null checks |
| Use Parallel Streams carefully | Better performance |
| Use CompletableFuture | Non-blocking execution |
| Use Date API | Thread-safe date handling |

---

# Real-World Applications

Java 8 best practices are followed in:

- Spring Boot applications
- REST APIs
- Banking systems
- E-commerce platforms
- Microservices
- Cloud-native applications

---

# Common Mistakes

### Long Lambda Expressions

Avoid putting complex business logic inside lambdas.

---

### Using Parallel Streams Everywhere

Parallel execution does not always improve performance.

---

### Using Optional as Entity Fields

Use Optional mainly for **method return types**.

---

### Ignoring Stream Readability

A simple loop is sometimes easier to understand than a complex stream pipeline.

---

# Best Practices Checklist

✔ Prefer Lambda Expressions

✔ Use Method References

✔ Keep Lambdas small

✔ Use Streams for collection processing

✔ Avoid reusing Streams

✔ Handle Optional safely

✔ Prefer Date & Time API

✔ Handle CompletableFuture exceptions

✔ Keep code readable

✔ Write immutable code where possible

---

# Summary

In this chapter, you learned:

- Lambda best practices
- Stream best practices
- Optional best practices
- CompletableFuture best practices
- Date & Time API recommendations
- Performance and readability guidelines

---

# Quick Revision

- Keep lambdas simple.
- Use Method References whenever possible.
- Do not reuse Streams.
- Avoid calling `Optional.get()`.
- Prefer the Java 8 Date API.
- Handle exceptions in `CompletableFuture`.
- Use Parallel Streams only when beneficial.
- Write readable, maintainable code.

---

# Practice Questions

### Basic

1. Why should lambdas be kept short?
2. What are Method References?
3. Why shouldn't a Stream be reused?
4. Why is `Optional.get()` discouraged?
5. When should Parallel Streams be used?

### Intermediate

6. Explain the benefits of immutable classes.
7. Compare traditional loops with Streams.
8. Why is readability important in Stream pipelines?

### Interview Questions

1. What are the most important Java 8 best practices?
2. How can Streams impact application performance?
3. When should you use `CompletableFuture`?
4. Why should `Optional` mainly be used as a return type?
5. What coding practices improve maintainability in Java 8?

---

# Hands-on Exercise

Create an **Employee Management System** that demonstrates Java 8 best practices by:

1. Using Lambda Expressions and Method References.
2. Processing employees with the Stream API.
3. Returning search results using `Optional`.
4. Formatting joining dates with the Date & Time API.
5. Loading employee statistics asynchronously using `CompletableFuture`.
6. Writing readable and maintainable stream pipelines.
7. Avoiding common Java 8 mistakes.
8. Documenting which best practices were applied and why.
