# Chapter 01: Annotations

## 📖 Overview

**Annotations** provide metadata about Java code. They give additional information to the compiler, JVM, or frameworks without changing the program's business logic.

Annotations are heavily used in modern Java frameworks like **Spring Boot**, **Hibernate**, **JUnit**, and **Jakarta EE**.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand annotations
- Use built-in annotations
- Create custom annotations
- Apply annotations at runtime
- Understand annotation retention policies
- Learn annotation best practices

---

# What are Annotations?

Annotations are metadata attached to Java elements such as:

- Classes
- Methods
- Fields
- Constructors
- Parameters
- Packages

They begin with the `@` symbol.

Example:

```java
@Override
public String toString() {

    return "Employee";
}
```

Here, `@Override` tells the compiler that the method overrides a superclass method.

---

# Why Use Annotations?

Annotations help to:

- Improve code readability
- Reduce boilerplate code
- Configure frameworks
- Enable compile-time checks
- Provide runtime metadata

---

# Built-in Annotations

Java provides several predefined annotations.

| Annotation | Purpose |
|------------|---------|
| `@Override` | Indicates method overriding |
| `@Deprecated` | Marks obsolete code |
| `@SuppressWarnings` | Suppresses compiler warnings |
| `@FunctionalInterface` | Marks a functional interface |
| `@SafeVarargs` | Suppresses unsafe varargs warnings |

---

# @Override

```java
class Animal {

    void sound() {

        System.out.println("Animal");
    }
}

class Dog extends Animal {

    @Override
    void sound() {

        System.out.println("Dog");
    }
}
```

If the method signature is incorrect, the compiler reports an error.

---

# @Deprecated

Marks a method or class as outdated.

```java
class Calculator {

    @Deprecated
    void oldMethod() {

        System.out.println("Old Method");
    }
}
```

The compiler warns developers to use newer alternatives.

---

# @SuppressWarnings

Suppresses specific compiler warnings.

```java
@SuppressWarnings("unchecked")
List list = new ArrayList();
```

Use this annotation only when necessary.

---

# @FunctionalInterface

Indicates that an interface contains exactly one abstract method.

```java
@FunctionalInterface
interface Calculator {

    int add(int a, int b);
}
```

Adding another abstract method results in a compilation error.

---

# Creating a Custom Annotation

Annotations can also be created by developers.

```java
@interface Author {

    String name();
}
```

Usage:

```java
@Author(name = "Rahul")
class Employee {

}
```

---

# Annotation Elements

Annotations can contain multiple elements.

```java
@interface StudentInfo {

    int id();

    String name();

    String course();
}
```

Usage:

```java
@StudentInfo(
    id = 101,
    name = "Rahul",
    course = "Java"
)
class Student {

}
```

---

# Default Values

Annotation elements can have default values.

```java
@interface Developer {

    String role() default "Backend";
}
```

Usage:

```java
@Developer
class Employee {

}
```

---

# Meta-Annotations

Meta-annotations define how annotations behave.

| Annotation | Purpose |
|------------|---------|
| `@Target` | Specifies where an annotation can be used |
| `@Retention` | Specifies how long an annotation is retained |
| `@Documented` | Includes annotation in Javadoc |
| `@Inherited` | Allows subclasses to inherit annotations |
| `@Repeatable` | Allows multiple uses of the same annotation |

---

# @Target

Restricts where an annotation can be applied.

```java
@Target(ElementType.METHOD)
@interface TestMethod {

}
```

Now the annotation can only be used on methods.

---

# @Retention

Defines the annotation lifecycle.

```java
@Retention(RetentionPolicy.RUNTIME)
@interface Author {

}
```

Retention policies:

| Policy | Description |
|---------|-------------|
| `SOURCE` | Available only during compilation |
| `CLASS` | Stored in `.class` file |
| `RUNTIME` | Available through Reflection |

---

# Using Reflection

Annotations are often read using Reflection.

```java
Class<Employee> cls = Employee.class;

if (cls.isAnnotationPresent(Author.class)) {

    Author author =
        cls.getAnnotation(Author.class);

    System.out.println(author.name());
}
```

---

# Common Annotation Workflow

```
Create Annotation
        │
        ▼
Apply Annotation
        │
        ▼
Compile Program
        │
        ▼
Read Using Reflection
        │
        ▼
Execute Logic
```

---

# Real-World Applications

Annotations are widely used in:

- Spring Boot (`@Component`, `@Service`)
- Spring MVC (`@RestController`)
- Hibernate (`@Entity`, `@Table`)
- JUnit (`@Test`)
- Dependency Injection
- Validation Frameworks

---

# Common Mistakes

### Forgetting Retention Policy

Without:

```java
@Retention(RetentionPolicy.RUNTIME)
```

Reflection cannot access the annotation at runtime.

---

### Incorrect Target

Using:

```java
@Target(ElementType.FIELD)
```

on a method causes a compilation error.

---

### Excessive Use of @SuppressWarnings

Suppress only the required warnings instead of hiding all compiler warnings.

---

# Best Practices

- Use built-in annotations whenever possible.
- Create custom annotations only when they add value.
- Choose the correct retention policy.
- Use meaningful annotation names.
- Keep annotation definitions simple.

---

# Summary

In this chapter, you learned:

- What annotations are
- Built-in annotations
- Custom annotations
- Meta-annotations
- Retention policies
- Reflection with annotations
- Best practices

---

# Quick Revision

- Annotations provide metadata.
- `@Override` verifies method overriding.
- `@Deprecated` marks obsolete code.
- `@FunctionalInterface` ensures one abstract method.
- `@Target` defines where annotations can be used.
- `@Retention` defines annotation lifetime.
- Reflection can read runtime annotations.

---

# Practice Questions

### Basic

1. What is an annotation?
2. Why are annotations used?
3. What does `@Override` do?
4. What is `@Deprecated`?
5. What is a custom annotation?

### Intermediate

6. Explain `@Target` and `@Retention`.
7. What are the different retention policies?
8. How are annotations accessed at runtime?

### Interview Questions

1. What are annotations in Java?
2. Differentiate built-in and custom annotations.
3. Explain meta-annotations with examples.
4. Why is `RetentionPolicy.RUNTIME` important?
5. How do frameworks like Spring use annotations?

---

# Hands-on Exercise

Create a **Student Annotation System** that:

1. Create a custom annotation `@StudentInfo`.
2. Add elements:
   - ID
   - Name
   - Course
3. Apply the annotation to a `Student` class.
4. Set the retention policy to `RUNTIME`.
5. Restrict usage to classes using `@Target`.
6. Use Reflection to read and display the annotation values.
7. Add another custom annotation with default values.
8. Compare built-in annotations with your custom annotations.
