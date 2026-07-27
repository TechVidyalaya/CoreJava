# Chapter 01: Introduction to Java 8

## 📖 Overview

**Java 8**, released in **March 2014**, is one of the most significant releases in Java history. It introduced **functional programming**, **Lambda Expressions**, **Stream API**, **Optional**, and the **new Date and Time API**, making Java code more concise, readable, and efficient.

Java 8 is still widely used in enterprise applications and is a must-know version for every Java developer.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand why Java 8 was introduced
- Learn the major features of Java 8
- Understand functional programming basics
- Explore Java 8 enhancements
- Prepare for upcoming Java 8 topics

---

# Why Java 8?

Before Java 8, Java programs were often:

- More verbose
- Difficult to process collections
- Limited support for functional programming
- More prone to `NullPointerException`
- Dependent on the old Date and Time API

Java 8 solved many of these limitations by introducing modern programming features.

---

# Major Features of Java 8

| Feature | Purpose |
|---------|---------|
| Lambda Expressions | Write concise anonymous functions |
| Functional Interfaces | Support functional programming |
| Method References | Simplify lambda expressions |
| Stream API | Process collections efficiently |
| Optional | Avoid `NullPointerException` |
| Date and Time API | Modern date and time handling |
| Default Methods | Add methods to interfaces without breaking existing implementations |
| Static Methods in Interfaces | Utility methods inside interfaces |
| Base64 API | Encode and decode data |
| CompletableFuture | Asynchronous programming |

---

# Evolution of Java

| Version | Highlights |
|---------|------------|
| Java 5 | Generics, Enhanced For Loop, Annotations |
| Java 7 | Try-with-Resources, NIO.2, Diamond Operator |
| **Java 8** | Lambda, Streams, Optional, Date-Time API |
| Java 9+ | Modules, JShell, HTTP Client, Records (later versions) |

---

# Traditional Java vs Java 8

### Before Java 8

```java
List<String> names = Arrays.asList(
        "Rahul", "Amit", "Neha");

for (String name : names) {

    System.out.println(name);
}
```

---

### Java 8

```java
List<String> names = Arrays.asList(
        "Rahul", "Amit", "Neha");

names.forEach(System.out::println);
```

Cleaner and easier to read.

---

# Functional Programming

Functional programming focuses on **what to do** instead of **how to do it**.

Example:

```java
numbers.stream()
       .filter(n -> n > 10)
       .forEach(System.out::println);
```

Instead of writing loops manually, operations are chained together.

---

# Java 8 Architecture

```
Java 8
│
├── Lambda Expressions
├── Functional Interfaces
├── Method References
├── Stream API
├── Optional
├── Date & Time API
├── Default Methods
├── Base64 API
└── CompletableFuture
```

---

# Benefits of Java 8

- Less boilerplate code
- Better readability
- Easier collection processing
- Improved performance with Streams
- Safer null handling
- Modern date and time support
- Better support for parallel programming

---

# Where Java 8 is Used

Java 8 is widely used in:

- Spring Boot applications
- REST APIs
- Microservices
- Banking software
- E-commerce platforms
- Enterprise applications
- Cloud-native applications

---

# Upcoming Chapters

In this module, you will learn:

1. Lambda Expressions
2. Functional Interfaces
3. Method References
4. Stream API
5. Stream Collectors
6. Optional Class
7. Date and Time API
8. Default & Static Methods
9. Base64 API
10. CompletableFuture Basics
11. Best Practices
12. Interview Questions
13. Mini Project

---

# Common Misconceptions

### Java 8 is only about Lambda Expressions

❌ Incorrect

Java 8 introduced many important APIs besides Lambdas, including Streams, Optional, and the new Date and Time API.

---

### Streams Modify Collections

❌ Incorrect

Streams process data without modifying the original collection unless explicitly updated.

---

# Best Practices

- Learn Lambda Expressions before Streams.
- Understand Functional Interfaces thoroughly.
- Prefer Streams for collection processing.
- Use Optional carefully; do not overuse it.
- Practice Java 8 features with real-world examples.

---

# Summary

In this chapter, you learned:

- Why Java 8 was introduced
- Major Java 8 features
- Functional programming basics
- Benefits of Java 8
- Real-world usage
- Overview of upcoming topics

---

# Quick Revision

- Java 8 was released in **2014**.
- It introduced functional programming to Java.
- Lambda Expressions reduce boilerplate code.
- Streams simplify collection processing.
- Optional helps avoid `NullPointerException`.
- The new Date and Time API replaces many limitations of older date classes.

---

# Practice Questions

### Basic

1. When was Java 8 released?
2. Why was Java 8 introduced?
3. Name five major Java 8 features.
4. What is functional programming?
5. What problem does Optional solve?

### Intermediate

6. Compare Java before and after Java 8.
7. Why is Stream API considered powerful?
8. What are the advantages of Lambda Expressions?

### Interview Questions

1. Why is Java 8 considered a milestone release?
2. What are the most important Java 8 features?
3. How does Java 8 improve code readability?
4. What is the relationship between Lambdas and Functional Interfaces?
5. Why do most enterprise projects still use Java 8 or later?

---

# Hands-on Exercise

Create a simple Java program that:

1. Print the installed Java version.
2. Create a list of five names.
3. Print the names using:
   - Enhanced `for` loop
   - `forEach()` method
4. Research three Java 8 features and write one practical use case for each.
5. Compare the traditional approach and the Java 8 approach for printing a collection.
