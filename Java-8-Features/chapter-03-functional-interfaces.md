# Chapter 03: Functional Interfaces

## 📖 Overview

A **Functional Interface** is an interface that contains **exactly one abstract method**. It is the foundation of **Lambda Expressions** and **Method References** introduced in Java 8.

Java provides many built-in functional interfaces in the `java.util.function` package, making functional programming easier and more expressive.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Functional Interfaces
- Create custom Functional Interfaces
- Use the `@FunctionalInterface` annotation
- Work with built-in Functional Interfaces
- Use Lambdas with Functional Interfaces

---

# What is a Functional Interface?

A Functional Interface contains **only one abstract method**.

Example:

```java
@FunctionalInterface
interface Greeting {

    void sayHello();
}
```

This interface can be implemented using a Lambda Expression.

```java
Greeting greeting = () -> System.out.println("Hello Java");

greeting.sayHello();
```

Output

```
Hello Java
```

---

# Characteristics

- Contains exactly one abstract method
- Can have multiple default methods
- Can have multiple static methods
- Can have methods inherited from `Object`
- Can be implemented using Lambda Expressions

---

# @FunctionalInterface Annotation

The `@FunctionalInterface` annotation tells the compiler that an interface is intended to be functional.

```java
@FunctionalInterface
interface Calculator {

    int add(int a, int b);
}
```

If another abstract method is added:

```java
@FunctionalInterface
interface Calculator {

    int add(int a, int b);

    int subtract(int a, int b);
}
```

Compile-time Error

```
Unexpected @FunctionalInterface annotation
```

---

# Without Lambda

```java
Calculator calculator = new Calculator() {

    @Override
    public int add(int a, int b) {

        return a + b;
    }
};

System.out.println(calculator.add(10, 20));
```

---

# Using Lambda

```java
Calculator calculator =
    (a, b) -> a + b;

System.out.println(calculator.add(10, 20));
```

Output

```
30
```

---

# Functional Interface with Default Method

```java
@FunctionalInterface
interface Greeting {

    void greet();

    default void welcome() {

        System.out.println("Welcome!");
    }
}
```

The interface remains functional because there is only **one abstract method**.

---

# Functional Interface with Static Method

```java
@FunctionalInterface
interface Greeting {

    void greet();

    static void info() {

        System.out.println("Java 8");
    }
}
```

---

# Built-in Functional Interfaces

Package:

```java
java.util.function
```

Common interfaces:

| Interface | Purpose |
|-----------|---------|
| `Predicate<T>` | Tests a condition |
| `Function<T, R>` | Converts one value into another |
| `Consumer<T>` | Consumes a value without returning anything |
| `Supplier<T>` | Supplies a value |

---

# Predicate

Returns `true` or `false`.

```java
Predicate<Integer> isEven =
    n -> n % 2 == 0;

System.out.println(isEven.test(10));
```

Output

```
true
```

---

# Function

Transforms one value into another.

```java
Function<String, Integer> length =
    text -> text.length();

System.out.println(length.apply("Java"));
```

Output

```
4
```

---

# Consumer

Consumes data without returning a result.

```java
Consumer<String> print =
    name -> System.out.println(name);

print.accept("Rahul");
```

Output

```
Rahul
```

---

# Supplier

Supplies a value without taking input.

```java
Supplier<Double> random =
    () -> Math.random();

System.out.println(random.get());
```

Example Output

```
0.847213
```

---

# Chaining Functional Interfaces

```java
Predicate<Integer> positive =
    n -> n > 0;

Predicate<Integer> even =
    n -> n % 2 == 0;

System.out.println(
    positive.and(even).test(20)
);
```

Output

```
true
```

---

# Functional Interfaces in Streams

```java
List<String> names =
    Arrays.asList("Rahul", "Neha", "Amit");

names.stream()
     .filter(name -> name.startsWith("R"))
     .forEach(System.out::println);
```

Output

```
Rahul
```

---

# Common Functional Interfaces

| Interface | Method |
|-----------|--------|
| `Predicate<T>` | `test()` |
| `Function<T,R>` | `apply()` |
| `Consumer<T>` | `accept()` |
| `Supplier<T>` | `get()` |
| `UnaryOperator<T>` | `apply()` |
| `BinaryOperator<T>` | `apply()` |

---

# Real-World Applications

Functional Interfaces are used in:

- Stream API
- Collection processing
- Event handling
- Multithreading
- Spring Boot
- Asynchronous programming

---

# Common Mistakes

### Multiple Abstract Methods

Incorrect:

```java
interface Demo {

    void m1();

    void m2();
}
```

This is **not** a Functional Interface.

---

### Forgetting @FunctionalInterface

The annotation is optional but recommended because it enables compile-time validation.

---

### Wrong Functional Interface

Use the appropriate interface:

- `Predicate` → Condition
- `Function` → Transformation
- `Consumer` → Output/Action
- `Supplier` → Generate Data

---

# Best Practices

- Use `@FunctionalInterface` whenever applicable.
- Prefer built-in Functional Interfaces over creating custom ones.
- Keep Lambda logic simple.
- Choose the correct interface based on the use case.
- Combine Functional Interfaces with Streams for cleaner code.

---

# Summary

In this chapter, you learned:

- Functional Interfaces
- `@FunctionalInterface`
- Built-in Functional Interfaces
- Predicate
- Function
- Consumer
- Supplier
- Best practices

---

# Quick Revision

- A Functional Interface has one abstract method.
- Lambda Expressions require Functional Interfaces.
- `Predicate` returns a boolean.
- `Function` transforms data.
- `Consumer` performs an action.
- `Supplier` provides data.
- `@FunctionalInterface` enables compile-time validation.

---

# Practice Questions

### Basic

1. What is a Functional Interface?
2. How many abstract methods can it have?
3. What is the purpose of `@FunctionalInterface`?
4. Which package contains built-in Functional Interfaces?
5. Name four built-in Functional Interfaces.

### Intermediate

6. Differentiate `Predicate` and `Function`.
7. Explain `Consumer` and `Supplier`.
8. Can a Functional Interface contain default methods? Explain.

### Interview Questions

1. Why are Functional Interfaces required for Lambda Expressions?
2. What happens if a Functional Interface contains two abstract methods?
3. Explain the purpose of `Predicate`, `Function`, `Consumer`, and `Supplier`.
4. What is the difference between `UnaryOperator` and `BinaryOperator`?
5. Why should built-in Functional Interfaces be preferred over custom ones?

---

# Hands-on Exercise

Create a program that:

1. Create a custom Functional Interface named `Calculator`.
2. Implement it using Lambda Expressions.
3. Use a `Predicate` to check whether a number is positive.
4. Use a `Function` to convert a string to uppercase.
5. Use a `Consumer` to print employee names.
6. Use a `Supplier` to generate a random number.
7. Display the output of all Functional Interfaces.
