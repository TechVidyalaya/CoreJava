# Chapter 17: Wrapper Classes

## 📖 Overview

Java provides **Wrapper Classes** to convert primitive data types into objects. Wrapper classes are useful when working with **Collections Framework**, **Generics**, and many Java APIs that require objects instead of primitive values.

Since Java 5, **Autoboxing** and **Unboxing** have made conversions between primitives and wrapper objects automatic.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand wrapper classes
- Convert primitives to objects
- Convert objects to primitives
- Understand Autoboxing and Unboxing
- Use commonly used wrapper class methods

---

# What are Wrapper Classes?

A Wrapper Class wraps a primitive data type into an object.

| Primitive | Wrapper Class |
|-----------|---------------|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

---

# Why Do We Need Wrapper Classes?

Primitive data types are not objects.

Many Java APIs require objects.

Example:

```java
ArrayList<int> numbers;
```

❌ Invalid

Correct:

```java
ArrayList<Integer> numbers = new ArrayList<>();
```

Wrapper classes make this possible.

---

# Creating Wrapper Objects

### Using `valueOf()`

```java
Integer number = Integer.valueOf(100);
```

---

### Using Autoboxing

```java
Integer number = 100;
```

Java automatically converts the primitive into an object.

---

# Autoboxing

Autoboxing is the automatic conversion of a primitive into its wrapper object.

```java
int age = 25;

Integer ageObject = age;
```

Equivalent to:

```java
Integer ageObject = Integer.valueOf(age);
```

---

# Unboxing

Unboxing is the automatic conversion of a wrapper object into a primitive.

```java
Integer marks = 90;

int score = marks;
```

Equivalent to:

```java
int score = marks.intValue();
```

---

# Parsing Strings

Wrapper classes can convert strings into primitive values.

### Integer

```java
String number = "100";

int value = Integer.parseInt(number);

System.out.println(value);
```

### Output

```
100
```

---

### Double

```java
String price = "99.99";

double amount = Double.parseDouble(price);

System.out.println(amount);
```

### Output

```
99.99
```

---

### Boolean

```java
String value = "true";

boolean result = Boolean.parseBoolean(value);

System.out.println(result);
```

### Output

```
true
```

---

# Converting Primitive to String

```java
int number = 100;

String text = String.valueOf(number);

System.out.println(text);
```

### Output

```
100
```

---

# Useful Integer Methods

### max()

```java
System.out.println(Integer.max(10, 20));
```

Output

```
20
```

---

### min()

```java
System.out.println(Integer.min(10, 20));
```

Output

```
10
```

---

### sum()

```java
System.out.println(Integer.sum(10, 20));
```

Output

```
30
```

---

### compare()

```java
System.out.println(Integer.compare(20, 10));
```

Output

```
1
```

---

# Useful Character Methods

### isDigit()

```java
System.out.println(Character.isDigit('5'));
```

Output

```
true
```

---

### isLetter()

```java
System.out.println(Character.isLetter('A'));
```

Output

```
true
```

---

### isUpperCase()

```java
System.out.println(Character.isUpperCase('J'));
```

Output

```
true
```

---

### toLowerCase()

```java
System.out.println(Character.toLowerCase('A'));
```

Output

```
a
```

---

# Useful Boolean Methods

```java
Boolean.parseBoolean("true");
Boolean.logicalAnd(true, false);
Boolean.logicalOr(true, false);
```

---

# Wrapper Classes in Collections

```java
import java.util.ArrayList;

public class Main {

    public static void main(String[] args) {

        ArrayList<Integer> numbers = new ArrayList<>();

        numbers.add(10);
        numbers.add(20);
        numbers.add(30);

        System.out.println(numbers);
    }
}
```

### Output

```
[10, 20, 30]
```

---

# Wrapper Class vs Primitive

| Primitive | Wrapper Class |
|-----------|---------------|
| Faster | Slightly slower |
| Less memory | More memory |
| Cannot be null | Can be null |
| Not an object | Object |
| Cannot be used in Generics | Can be used in Generics |

---

# Common Mistakes

### Comparing Wrapper Objects Using `==`

```java
Integer a = 200;
Integer b = 200;

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

Output

```
true
```

---

### Parsing Invalid Numbers

```java
Integer.parseInt("ABC");
```

❌ Throws:

```
NumberFormatException
```

---

### Forgetting Null Checks

```java
Integer number = null;

int value = number;
```

❌ Throws:

```
NullPointerException
```

---

# Best Practices

- Use primitives when object functionality is not required.
- Use wrapper classes in collections and generics.
- Prefer autoboxing and unboxing for cleaner code.
- Use `parseXXX()` methods carefully with valid input.
- Use `equals()` instead of `==` when comparing wrapper objects.

---

# Summary

In this chapter, you learned:

- Wrapper classes
- Autoboxing
- Unboxing
- Parsing strings
- Wrapper utility methods
- Wrapper classes in collections
- Best practices

---

# Quick Revision

- Wrapper classes convert primitives into objects.
- Java provides eight wrapper classes.
- Autoboxing converts primitive → object.
- Unboxing converts object → primitive.
- Collections require wrapper classes.
- Use `parseInt()` and similar methods to convert strings.

---

# Practice Questions

### Basic

1. What is a wrapper class?
2. Why are wrapper classes required?
3. What is autoboxing?
4. What is unboxing?
5. Which wrapper class corresponds to `int`?

### Intermediate

6. Explain the difference between primitives and wrapper classes.
7. How does `Integer.parseInt()` work?
8. Why can't generics use primitive data types?

### Interview Questions

1. What is the difference between `Integer.valueOf()` and `Integer.parseInt()`?
2. Why do wrapper classes exist in Java?
3. Explain autoboxing and unboxing with examples.
4. Why should wrapper objects be compared using `equals()`?
5. When should you use primitives instead of wrapper classes?

---

# Hands-on Exercise

Create a program that:

1. Accepts an integer as a String.
2. Convert it into an `Integer` using `parseInt()`.
3. Store it in an `ArrayList<Integer>`.
4. Add five numbers to the list.
5. Find the maximum and minimum values using `Integer.max()` and `Integer.min()`.
6. Print the list and the calculated results.
