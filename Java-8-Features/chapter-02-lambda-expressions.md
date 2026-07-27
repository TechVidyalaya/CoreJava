# Chapter 02: Lambda Expressions

## 📖 Overview

**Lambda Expressions** are one of the most important features introduced in **Java 8**. They allow you to write **anonymous functions** (functions without a name), making code shorter, cleaner, and easier to read.

Lambda Expressions are mainly used with **Functional Interfaces**, the **Stream API**, and event handling.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Lambda Expressions
- Learn the syntax of Lambdas
- Convert anonymous classes into Lambdas
- Use Lambdas with Functional Interfaces
- Write cleaner and more concise Java code

---

# What is a Lambda Expression?

A Lambda Expression is an **anonymous function** that can be passed as an argument to a method.

Instead of writing:

```java
public void display() {
    System.out.println("Hello");
}
```

You can write:

```java
() -> System.out.println("Hello");
```

---

# Lambda Expression Syntax

```java
(parameters) -> expression
```

or

```java
(parameters) -> {
    // multiple statements
}
```

General syntax:

```java
(parameter1, parameter2) -> {
    // code
}
```

---

# Why Lambda Expressions?

Before Java 8, anonymous classes were commonly used.

Example:

```java
Runnable task = new Runnable() {

    @Override
    public void run() {

        System.out.println("Task Running");
    }
};
```

With Lambda:

```java
Runnable task =
    () -> System.out.println("Task Running");
```

Much shorter and easier to read.

---

# Lambda with No Parameters

```java
Runnable task = () -> {

    System.out.println("Hello Java");
};

task.run();
```

Output

```
Hello Java
```

---

# Lambda with One Parameter

```java
interface Message {

    void print(String name);
}

Message msg =
    name -> System.out.println("Hello " + name);

msg.print("Rahul");
```

Output

```
Hello Rahul
```

---

# Lambda with Multiple Parameters

```java
interface Calculator {

    int add(int a, int b);
}

Calculator calc =
    (a, b) -> a + b;

System.out.println(calc.add(10, 20));
```

Output

```
30
```

---

# Lambda with Multiple Statements

```java
Calculator calc = (a, b) -> {

    int result = a + b;

    return result;
};
```

Braces and `return` are required when using multiple statements.

---

# Using Lambda with Collections

Traditional approach:

```java
List<String> names =
    Arrays.asList("Rahul", "Neha", "Amit");

for (String name : names) {

    System.out.println(name);
}
```

Using Lambda:

```java
names.forEach(name ->
    System.out.println(name));
```

Or

```java
names.forEach(System.out::println);
```

---

# Lambda with Thread

```java
Thread thread = new Thread(() -> {

    System.out.println("Thread Running");
});

thread.start();
```

---

# Lambda with Comparator

Before Java 8:

```java
Collections.sort(list,
    new Comparator<String>() {

        @Override
        public int compare(
                String a,
                String b) {

            return a.compareTo(b);
        }
    });
```

Using Lambda:

```java
Collections.sort(
    list,
    (a, b) -> a.compareTo(b)
);
```

---

# Lambda with Streams

```java
List<Integer> numbers =
    Arrays.asList(10, 20, 30);

numbers.stream()
       .forEach(n ->
           System.out.println(n));
```

---

# Rules for Lambda Expressions

- Lambda works only with **Functional Interfaces**.
- Parameter types are usually inferred.
- Parentheses are optional for a single parameter.
- Braces are optional for a single expression.
- Lambdas cannot be instantiated directly.

---

# Advantages of Lambda Expressions

- Less boilerplate code
- Improved readability
- Easier collection processing
- Better support for functional programming
- Simplifies anonymous classes

---

# Real-World Applications

Lambda Expressions are commonly used in:

- Stream API
- Collection sorting
- Event handling
- Multithreading
- Asynchronous programming
- Spring Boot applications

---

# Common Mistakes

### Using Lambda with Non-Functional Interfaces

Incorrect:

```java
interface Test {

    void m1();

    void m2();
}
```

Lambda cannot be used because there are two abstract methods.

---

### Forgetting Return Value

Incorrect:

```java
(a, b) -> {

    a + b;
}
```

Correct:

```java
(a, b) -> {

    return a + b;
}
```

---

### Unnecessary Braces

Instead of:

```java
(a, b) -> {

    return a + b;
}
```

Use:

```java
(a, b) -> a + b
```

For a single expression.

---

# Best Practices

- Keep Lambda Expressions short and readable.
- Use Method References when they improve readability.
- Avoid complex business logic inside Lambdas.
- Use meaningful parameter names.
- Prefer Streams with Lambdas for collection processing.

---

# Summary

In this chapter, you learned:

- Lambda Expressions
- Lambda syntax
- Anonymous class conversion
- Lambda with collections
- Lambda with threads
- Lambda with Comparator
- Best practices

---

# Quick Revision

- Lambda Expressions were introduced in Java 8.
- They represent anonymous functions.
- Lambdas work only with Functional Interfaces.
- `->` is called the Lambda operator.
- Parentheses and braces can often be omitted.
- Lambdas reduce boilerplate code.

---

# Practice Questions

### Basic

1. What is a Lambda Expression?
2. Which Java version introduced Lambdas?
3. What symbol is used in Lambda Expressions?
4. Can Lambdas work with any interface?
5. What is the benefit of Lambdas?

### Intermediate

6. Explain the syntax of a Lambda Expression.
7. Convert an anonymous class into a Lambda.
8. When are braces required in a Lambda?

### Interview Questions

1. What is the difference between an anonymous class and a Lambda Expression?
2. Why do Lambda Expressions require Functional Interfaces?
3. Can Lambda Expressions access local variables?
4. How are Lambda Expressions used with Streams?
5. What are the advantages of Lambda Expressions in enterprise applications?

---

# Hands-on Exercise

Create a program that:

1. Create a `Calculator` Functional Interface.
2. Implement:
   - Addition
   - Subtraction
   - Multiplication
   - Division
   using Lambda Expressions.
3. Create a list of employee names.
4. Print the names using:
   - `forEach()`
   - Lambda Expression
   - Method Reference
5. Create a thread using a Lambda Expression and print a message from the new thread.
