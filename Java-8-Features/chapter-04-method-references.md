# Chapter 04: Method References

## 📖 Overview

**Method References** were introduced in **Java 8** to make Lambda Expressions even more concise and readable. Instead of writing a Lambda that simply calls an existing method, you can directly reference that method.

Method References are widely used with **Streams**, **Collections**, and **Functional Interfaces**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Method References
- Learn the syntax of Method References
- Use different types of Method References
- Replace simple Lambda Expressions with Method References
- Improve code readability

---

# What is a Method Reference?

A Method Reference is a shorthand notation for a Lambda Expression that calls an existing method.

Instead of:

```java
name -> System.out.println(name)
```

You can write:

```java
System.out::println
```

The `::` operator is called the **Method Reference Operator**.

---

# Syntax

```java
ClassName::methodName
```

or

```java
objectReference::methodName
```

or

```java
ClassName::new
```

---

# Why Use Method References?

Lambda Expression:

```java
names.forEach(name ->
    System.out.println(name));
```

Method Reference:

```java
names.forEach(System.out::println);
```

Both produce the same result, but the second is cleaner.

---

# Types of Method References

Java supports four types:

| Type | Example |
|------|---------|
| Static Method | `Math::max` |
| Instance Method of an Object | `printer::print` |
| Instance Method of an Arbitrary Object | `String::toUpperCase` |
| Constructor Reference | `Student::new` |

---

# Static Method Reference

```java
class Calculator {

    public static int square(int n) {

        return n * n;
    }
}
```

Using Lambda:

```java
Function<Integer, Integer> function =
    n -> Calculator.square(n);
```

Using Method Reference:

```java
Function<Integer, Integer> function =
    Calculator::square;
```

---

# Instance Method Reference (Particular Object)

```java
class Printer {

    public void print(String message) {

        System.out.println(message);
    }
}

Printer printer = new Printer();

Consumer<String> consumer =
    printer::print;

consumer.accept("Hello Java");
```

Output

```
Hello Java
```

---

# Instance Method Reference (Arbitrary Object)

```java
Function<String, String> upper =
    String::toUpperCase;

System.out.println(
    upper.apply("java")
);
```

Output

```
JAVA
```

---

# Constructor Reference

```java
class Student {

    Student() {

        System.out.println("Student Created");
    }
}
```

```java
Supplier<Student> supplier =
    Student::new;

supplier.get();
```

Output

```
Student Created
```

---

# Method Reference with Collections

Lambda:

```java
List<String> names =
    Arrays.asList("Rahul", "Neha", "Amit");

names.forEach(name ->
    System.out.println(name));
```

Method Reference:

```java
names.forEach(System.out::println);
```

---

# Method Reference with Stream API

```java
List<String> names =
    Arrays.asList("java", "spring", "boot");

names.stream()
     .map(String::toUpperCase)
     .forEach(System.out::println);
```

Output

```
JAVA
SPRING
BOOT
```

---

# Lambda vs Method Reference

Lambda:

```java
x -> x.length()
```

Method Reference:

```java
String::length
```

---

Lambda:

```java
x -> Math.abs(x)
```

Method Reference:

```java
Math::abs
```

---

# When to Use Method References

Use Method References when:

- The Lambda only calls an existing method.
- No additional logic is required.
- Readability improves.

Use Lambdas when additional processing is needed.

---

# Advantages

- Shorter code
- Better readability
- Less boilerplate
- Easy integration with Streams
- Cleaner functional programming

---

# Real-World Applications

Method References are commonly used in:

- Stream API
- Collection processing
- Sorting
- Event handling
- Spring Boot applications
- Functional programming

---

# Common Mistakes

### Using Method References for Complex Logic

Incorrect:

```java
name ->
    name.trim().toUpperCase()
```

Cannot be replaced with a single Method Reference because multiple operations are involved.

---

### Incorrect Method Signature

The referenced method must match the Functional Interface method signature.

Example:

```java
Function<String, Integer> length =
    String::length;
```

Works because `length()` returns an `int`.

---

### Overusing Method References

If a Method Reference makes the code less clear, use a Lambda instead.

---

# Best Practices

- Use Method References only when they improve readability.
- Prefer Method References over simple Lambdas.
- Use Constructor References for object creation.
- Keep Functional Interface signatures compatible.
- Combine Method References with Streams for cleaner code.

---

# Summary

In this chapter, you learned:

- Method References
- Method Reference syntax
- Static Method References
- Instance Method References
- Constructor References
- Lambda vs Method Reference
- Best practices

---

# Quick Revision

- Method References use the `::` operator.
- They are shorthand for simple Lambda Expressions.
- Java supports four types of Method References.
- Constructor References use `ClassName::new`.
- Method References work with Functional Interfaces.
- Streams commonly use Method References.

---

# Practice Questions

### Basic

1. What is a Method Reference?
2. Which operator is used for Method References?
3. Name the four types of Method References.
4. What is a Constructor Reference?
5. When should Method References be used?

### Intermediate

6. Differentiate Lambda Expressions and Method References.
7. Explain the different types of Method References with examples.
8. Can every Lambda Expression be replaced by a Method Reference? Why?

### Interview Questions

1. What are Method References in Java 8?
2. What is the difference between `ClassName::method` and `object::method`?
3. Explain Constructor References with an example.
4. When should you prefer a Lambda over a Method Reference?
5. How do Method References improve code readability?

---

# Hands-on Exercise

Create a program that:

1. Create a list of employee names.
2. Print the names using:
   - Lambda Expression
   - Method Reference
3. Convert all names to uppercase using `String::toUpperCase`.
4. Create a static method to calculate the square of a number and invoke it using a Method Reference.
5. Create a `Student` class and instantiate objects using a Constructor Reference.
6. Compare the output of Lambda Expressions and Method References.
