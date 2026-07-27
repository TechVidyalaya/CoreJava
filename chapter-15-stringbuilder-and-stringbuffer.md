# Chapter 15: StringBuilder and StringBuffer

## 📖 Overview

Both **StringBuilder** and **StringBuffer** are mutable classes used to modify strings efficiently. Unlike the `String` class, they allow changes without creating a new object every time.

- **StringBuilder** is faster but **not thread-safe**.
- **StringBuffer** is thread-safe but slightly slower.

These classes are part of the `java.lang` package.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand mutable strings
- Differentiate String, StringBuilder, and StringBuffer
- Use commonly used methods
- Choose the appropriate class for different scenarios

---

# Why Do We Need StringBuilder?

Consider the following example:

```java
String str = "Java";

str = str + " Programming";
str = str + " Language";
str = str + " Course";
```

Each concatenation creates a **new String object**, leading to unnecessary memory usage.

A better approach is:

```java
StringBuilder sb = new StringBuilder();

sb.append("Java");
sb.append(" Programming");
sb.append(" Language");
```

Only one object is modified.

---

# StringBuilder

`StringBuilder` is a mutable sequence of characters.

### Creating a StringBuilder

```java
StringBuilder sb = new StringBuilder();
```

Or

```java
StringBuilder sb = new StringBuilder("Java");
```

---

# append()

Adds text at the end.

```java
StringBuilder sb = new StringBuilder("Java");

sb.append(" Programming");

System.out.println(sb);
```

### Output

```
Java Programming
```

---

# insert()

Inserts text at a specified position.

```java
StringBuilder sb = new StringBuilder("Jva");

sb.insert(1, "a");

System.out.println(sb);
```

### Output

```
Java
```

---

# replace()

Replaces characters.

```java
StringBuilder sb = new StringBuilder("Java");

sb.replace(0, 4, "Spring");

System.out.println(sb);
```

### Output

```
Spring
```

---

# delete()

Removes characters.

```java
StringBuilder sb = new StringBuilder("Java Programming");

sb.delete(4, 16);

System.out.println(sb);
```

### Output

```
Java
```

---

# reverse()

Reverses the text.

```java
StringBuilder sb = new StringBuilder("Java");

sb.reverse();

System.out.println(sb);
```

### Output

```
avaJ
```

---

# length()

Returns the number of characters.

```java
StringBuilder sb = new StringBuilder("Java");

System.out.println(sb.length());
```

### Output

```
4
```

---

# charAt()

Returns a character at a given index.

```java
System.out.println(sb.charAt(2));
```

### Output

```
v
```

---

# setCharAt()

Changes a character.

```java
StringBuilder sb = new StringBuilder("Java");

sb.setCharAt(0, 'L');

System.out.println(sb);
```

### Output

```
Lava
```

---

# toString()

Converts a StringBuilder into a String.

```java
StringBuilder sb = new StringBuilder("Java");

String str = sb.toString();
```

---

# StringBuffer

`StringBuffer` provides the same functionality as `StringBuilder`.

Example:

```java
StringBuffer sb = new StringBuffer("Java");

sb.append(" Course");

System.out.println(sb);
```

### Output

```
Java Course
```

---

# StringBuilder vs StringBuffer

| StringBuilder | StringBuffer |
|---------------|--------------|
| Faster | Slightly slower |
| Not thread-safe | Thread-safe |
| Java 5 | Java 1.0 |
| Recommended for single-threaded programs | Recommended for multi-threaded programs |

---

# String vs StringBuilder vs StringBuffer

| Feature | String | StringBuilder | StringBuffer |
|---------|--------|---------------|--------------|
| Mutable | ❌ No | ✅ Yes | ✅ Yes |
| Thread-safe | ✅ Yes | ❌ No | ✅ Yes |
| Performance | Slow for frequent changes | Fast | Moderate |
| Memory Efficient | No | Yes | Yes |

---

# Method Chaining

Most methods return the same object, allowing chaining.

```java
StringBuilder sb = new StringBuilder();

sb.append("Java")
  .append(" ")
  .append("Spring")
  .append(" Boot");

System.out.println(sb);
```

### Output

```
Java Spring Boot
```

---

# Real-World Example

Generating a CSV record.

```java
StringBuilder csv = new StringBuilder();

csv.append("101")
   .append(",")
   .append("Rahul")
   .append(",")
   .append("Developer");

System.out.println(csv);
```

### Output

```
101,Rahul,Developer
```

---

# Common Mistakes

### Using String for Repeated Concatenation

```java
String result = "";

for (int i = 0; i < 1000; i++) {
    result += i;
}
```

❌ Inefficient.

Use:

```java
StringBuilder result = new StringBuilder();
```

---

### Forgetting `toString()`

```java
StringBuilder sb = new StringBuilder("Java");

String text = sb.toString();
```

Convert to `String` when required.

---

### Choosing StringBuffer Unnecessarily

Use `StringBuffer` only when thread safety is required.

Otherwise, prefer `StringBuilder`.

---

# Best Practices

- Use `String` for fixed text.
- Use `StringBuilder` for frequent modifications.
- Use `StringBuffer` only in multi-threaded scenarios.
- Prefer method chaining for better readability.
- Convert to `String` only when needed.

---

# Summary

In this chapter, you learned:

- Mutable strings
- StringBuilder
- StringBuffer
- Common methods
- Method chaining
- Performance comparison

---

# Quick Revision

- `String` is immutable.
- `StringBuilder` is mutable and fast.
- `StringBuffer` is mutable and thread-safe.
- Use `append()` instead of repeated `+`.
- Convert using `toString()` when required.

---

# Practice Questions

### Basic

1. What is the difference between String and StringBuilder?
2. Is StringBuilder mutable?
3. Which class is thread-safe?
4. Which method adds text to the end?
5. What does `reverse()` do?

### Intermediate

6. Explain the difference between StringBuilder and StringBuffer.
7. Why is StringBuilder faster than String?
8. When should you use StringBuffer?

### Interview Questions

1. Why is StringBuilder preferred over String for concatenation?
2. What is method chaining?
3. Is StringBuilder thread-safe?
4. Can StringBuilder be converted to String?
5. Which class would you choose for building large JSON or SQL queries?

---

# Hands-on Exercise

Create a program that:

1. Creates a `StringBuilder` with the text `"Tech"`.
2. Append `" Vidyalaya"`.
3. Insert `"Java "` after `"Tech "`.
4. Replace `"Vidyalaya"` with `"Academy"`.
5. Reverse the final string.
6. Convert it into a `String` and display the result.
