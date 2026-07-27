# Chapter 14: String Class

## 📖 Overview

A **String** is a sequence of characters used to store and manipulate text. In Java, `String` is one of the most commonly used classes and is part of the `java.lang` package.

One of the most important characteristics of a String is that it is **immutable**, meaning its value cannot be changed after it is created.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the String class
- Create String objects
- Understand String immutability
- Compare Strings correctly
- Use commonly used String methods
- Understand String Pool

---

# What is a String?

A String represents a sequence of characters.

Examples:

```text
"Java"
"Hello World"
"TechVidyalaya"
```

---

# Creating Strings

## Using String Literal

```java
String language = "Java";
```

Java stores string literals in the **String Pool**.

---

## Using `new`

```java
String language = new String("Java");
```

This always creates a new object in heap memory.

---

# String Pool

Java maintains a special memory area called the **String Pool**.

```java
String s1 = "Java";
String s2 = "Java";
```

Both variables refer to the same object.

```
String Pool

+---------+
| "Java"  |
+---------+
   ▲   ▲
   │   │
  s1  s2
```

---

# Using `new`

```java
String s1 = new String("Java");
String s2 = new String("Java");
```

Here, two separate objects are created.

```
Heap

+---------+
| "Java"  | ← s1
+---------+

+---------+
| "Java"  | ← s2
+---------+
```

---

# String Immutability

Strings cannot be modified after creation.

```java
String name = "Java";

name.concat(" Programming");

System.out.println(name);
```

### Output

```
Java
```

The original String remains unchanged.

Correct:

```java
name = name.concat(" Programming");
```

Output

```
Java Programming
```

---

# Why are Strings Immutable?

- Thread safety
- Security
- Better performance
- String Pool optimisation
- Safe use as HashMap keys

---

# Comparing Strings

## Using `==`

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

### Output

```
true
```

Because both references point to the same object.

---

## Using `equals()`

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1.equals(s2));
```

### Output

```
true
```

`equals()` compares the contents.

---

## `==` vs `equals()`

| `==` | `equals()` |
|-------|------------|
| Compares references | Compares contents |
| Checks memory location | Checks character values |

---

# Common String Methods

## length()

```java
String str = "Java";

System.out.println(str.length());
```

Output

```
4
```

---

## charAt()

```java
System.out.println(str.charAt(1));
```

Output

```
a
```

---

## substring()

```java
String str = "Programming";

System.out.println(str.substring(3));
```

Output

```
gramming
```

```java
System.out.println(str.substring(3, 7));
```

Output

```
gram
```

---

## toUpperCase()

```java
System.out.println(str.toUpperCase());
```

Output

```
PROGRAMMING
```

---

## toLowerCase()

```java
System.out.println(str.toLowerCase());
```

Output

```
programming
```

---

## contains()

```java
System.out.println(str.contains("gram"));
```

Output

```
true
```

---

## startsWith()

```java
System.out.println(str.startsWith("Pro"));
```

Output

```
true
```

---

## endsWith()

```java
System.out.println(str.endsWith("ing"));
```

Output

```
true
```

---

## indexOf()

```java
System.out.println(str.indexOf("g"));
```

Output

```
3
```

---

## lastIndexOf()

```java
System.out.println(str.lastIndexOf("g"));
```

Output

```
10
```

---

## replace()

```java
String text = "Java";

System.out.println(text.replace("Java", "Spring"));
```

Output

```
Spring
```

---

## trim()

```java
String name = "  Rahul  ";

System.out.println(name.trim());
```

Output

```
Rahul
```

---

## isEmpty()

```java
String s = "";

System.out.println(s.isEmpty());
```

Output

```
true
```

---

## isBlank() (Java 11)

```java
String s = "   ";

System.out.println(s.isBlank());
```

Output

```
true
```

---

## split()

```java
String sentence = "Java,Python,SQL";

String[] courses = sentence.split(",");
```

Output

```
Java
Python
SQL
```

---

## join()

```java
String result = String.join("-", "Java", "Spring", "SQL");

System.out.println(result);
```

Output

```
Java-Spring-SQL
```

---

# String Memory Example

```java
String a = "Hello";
String b = "Hello";
String c = new String("Hello");
```

```
String Pool

"Hello"
 ▲     ▲
 │     │
 a     b

Heap

"Hello"
 ▲
 │
 c
```

---

# Common Mistakes

### Using `==`

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);
```

Output

```
false
```

Correct:

```java
System.out.println(a.equals(b));
```

---

### Forgetting Immutability

```java
String s = "Java";

s.toUpperCase();

System.out.println(s);
```

Output

```
Java
```

Assign the result back if modification is required.

---

# Best Practices

- Prefer String literals whenever possible.
- Use `equals()` to compare Strings.
- Remember that Strings are immutable.
- Use `isBlank()` instead of `trim().isEmpty()` when using Java 11+.
- Use `StringBuilder` for frequent modifications.

---

# Summary

In this chapter, you learned:

- String creation
- String Pool
- Immutability
- String comparison
- Frequently used String methods
- Memory representation

---

# Quick Revision

- `String` belongs to `java.lang`.
- Strings are immutable.
- String literals use the String Pool.
- `==` compares references.
- `equals()` compares content.
- Use `StringBuilder` for mutable text operations.

---

# Practice Questions

### Basic

1. What is a String?
2. What is String immutability?
3. What is the String Pool?
4. What is the difference between `==` and `equals()`?
5. Which package contains the String class?

### Intermediate

6. Why are Strings immutable?
7. Explain the difference between String literals and objects created using `new`.
8. Explain the String Pool with an example.

### Interview Questions

1. Why is String immutable in Java?
2. Why is String a good key for `HashMap`?
3. What is the difference between `isEmpty()` and `isBlank()`?
4. How does the String Pool improve performance?
5. When should you use `StringBuilder` instead of `String`?

---

# Hands-on Exercise

Create a program that:

1. Accepts a user's full name.
2. Displays:
   - Original name
   - Uppercase
   - Lowercase
   - Length
   - First character
   - Last character
3. Check whether the name starts with a given prefix.
4. Replace all spaces with underscores (`_`).
5. Split the name into individual words and print each word separately.
