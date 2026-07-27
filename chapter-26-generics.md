# Chapter 26: Generics

## 📖 Overview

**Generics** allow you to write classes, interfaces, and methods that work with different data types while providing **compile-time type safety**.

Before Generics (Java 5), collections stored objects as `Object`, requiring explicit type casting. Generics eliminate unnecessary casting and reduce runtime errors.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Generics
- Use Generic classes
- Create Generic methods
- Apply bounded Generics
- Understand wildcard types
- Learn the advantages of Generics

---

# What are Generics?

Generics allow a class or method to work with different data types using **type parameters**.

Example:

```java
List<String> names = new ArrayList<>();

List<Integer> numbers = new ArrayList<>();
```

Here, `String` and `Integer` are type arguments.

---

# Why Do We Need Generics?

Without Generics:

```java
ArrayList list = new ArrayList();

list.add("Java");
list.add(100);

String value = (String) list.get(0);
```

Problems:

- No compile-time type checking
- Explicit casting required
- Higher chance of `ClassCastException`

---

With Generics:

```java
ArrayList<String> list = new ArrayList<>();

list.add("Java");

// list.add(100); ❌ Compile-time error

String value = list.get(0);
```

---

# Generic Class

```java
class Box<T> {

    private T value;

    public void set(T value) {
        this.value = value;
    }

    public T get() {
        return value;
    }
}
```

Using the class:

```java
Box<String> box = new Box<>();

box.set("Java");

System.out.println(box.get());
```

### Output

```
Java
```

---

# Using Different Data Types

```java
Box<Integer> numberBox = new Box<>();

numberBox.set(100);

System.out.println(numberBox.get());
```

### Output

```
100
```

---

# Multiple Type Parameters

```java
class Pair<K, V> {

    private K key;
    private V value;

    public Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }

    public K getKey() {
        return key;
    }

    public V getValue() {
        return value;
    }
}
```

Usage:

```java
Pair<Integer, String> student =
        new Pair<>(101, "Rahul");
```

---

# Generic Method

A method can also use Generics.

```java
public class Utility {

    public static <T> void print(T value) {

        System.out.println(value);
    }
}
```

Usage:

```java
Utility.print("Java");
Utility.print(100);
Utility.print(99.5);
```

---

# Bounded Generics

Restrict Generics to a specific type or its subclasses.

```java
class Calculator<T extends Number> {

    private T value;

    Calculator(T value) {
        this.value = value;
    }

    public double square() {
        return value.doubleValue() * value.doubleValue();
    }
}
```

Usage:

```java
Calculator<Integer> c = new Calculator<>(10);

System.out.println(c.square());
```

### Output

```
100.0
```

---

# Wildcards

Wildcards are represented using `?`.

## Unbounded Wildcard

```java
List<?> list;
```

Can reference a list of any type.

---

## Upper Bounded Wildcard

```java
List<? extends Number> numbers;
```

Accepts:

- Integer
- Double
- Float
- Long

---

## Lower Bounded Wildcard

```java
List<? super Integer> numbers;
```

Accepts:

- Integer
- Number
- Object

---

# Generic Interface

```java
interface Repository<T> {

    void save(T object);

    T findById(int id);
}
```

---

# Type Erasure

Java removes Generic type information during compilation.

Example:

```java
List<String>
```

Becomes:

```java
List
```

This process is called **Type Erasure**.

---

# Advantages of Generics

- Compile-time type checking
- Eliminates explicit casting
- Code reusability
- Better readability
- Reduces runtime errors

---

# Real-World Examples

Generics are used in:

```java
ArrayList<String>

HashMap<Integer, String>

Optional<User>

Comparator<Employee>
```

Almost every modern Java framework uses Generics extensively.

---

# Common Mistakes

### Using Raw Types

Incorrect:

```java
ArrayList list = new ArrayList();
```

Correct:

```java
ArrayList<String> list = new ArrayList<>();
```

---

### Mixing Data Types

```java
List<String> names = new ArrayList<>();

names.add("Java");

// names.add(100); ❌ Compile-time error
```

---

### Using Primitive Types

Incorrect:

```java
List<int> numbers;
```

Correct:

```java
List<Integer> numbers;
```

Generics work only with reference types.

---

# Best Practices

- Always use Generics with collections.
- Avoid raw types.
- Use meaningful type parameter names (`T`, `E`, `K`, `V`).
- Use bounded Generics when restrictions are required.
- Prefer compile-time type safety over explicit casting.

---

# Summary

In this chapter, you learned:

- Generic classes
- Generic methods
- Multiple type parameters
- Bounded Generics
- Wildcards
- Type Erasure
- Best practices

---

# Quick Revision

- Generics provide type safety.
- `T` represents a type parameter.
- Generic methods work with multiple data types.
- `extends` creates upper bounds.
- `?` represents a wildcard.
- Generics reduce `ClassCastException`.

---

# Practice Questions

### Basic

1. What are Generics?
2. Why are Generics used?
3. What is a type parameter?
4. What is a Generic class?
5. Can Generics work with primitive types?

### Intermediate

6. Explain bounded Generics.
7. What are wildcards?
8. What is Type Erasure?

### Interview Questions

1. What are the advantages of Generics?
2. Why can't Generics use primitive data types?
3. Explain the difference between `?`, `? extends`, and `? super`.
4. What is Type Erasure in Java?
5. What are raw types, and why should they be avoided?

---

# Hands-on Exercise

Create a Generic class named `Storage<T>` that:

1. Stores any type of object.
2. Provides `set()` and `get()` methods.
3. Create objects for:
   - `String`
   - `Integer`
   - `Double`
4. Create a Generic method to print any value.
5. Create a `Pair<K, V>` class to store a Student ID and Student Name.
6. Demonstrate the use of an upper bounded Generic using `Number`.
